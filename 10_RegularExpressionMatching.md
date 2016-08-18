# 10. Regular Expression Matching

## 题目
'.' Matches any single character.
'*' Matches zero or more of the preceding element.

The matching should cover the entire input string (not partial).

The function prototype should be:
bool isMatch(const char *s, const char *p)

Some examples:
isMatch("aa","a") → false
isMatch("aa","aa") → true
isMatch("aaa","aa") → false
isMatch("aa", "a*") → true
isMatch("aa", ".*") → true
isMatch("ab", ".*") → true
isMatch("aab", "c* a *b") → true
## 代码
递归的方法

	public boolean isMatch(String s, String p) {
    	if (p.isEmpty()) {
        	return s.isEmpty();
    	}
		//p的字符串长度为1
    	if (p.length() == 1 || p.charAt(1) != '*') {
        	if (s.isEmpty() || (p.charAt(0) != '.' && p.charAt(0) != s.charAt(0))) {
            	return false;
        	} else {
            	return isMatch(s.substring(1), p.substring(1));
        	}
    	}

    	//P.length() >=2
    	while (!s.isEmpty() && (s.charAt(0) == p.charAt(0) || p.charAt(0) == '.')) {  
        	if (isMatch(s, p.substring(2))) { 
            	return true;                     
        	}                                    
        	s = s.substring(1);
    	}

    	return isMatch(s, p.substring(2));
	}


第二种解法：利用二维数组方法。建立布尔类型的二维数组，其值代表是否匹配。

	public boolean isMatch(String s, String p) {
    /*
    f(i,j) s中的i位置和p中j位置匹配
    f(i,j) =
        if (p_j-1 != * ) f(i-1, j-1) and s_i-1 等于 p_j-1
        if (p_j-1 == * )
      		* 匹配0次时: f(i,j-2)
            or * 匹配至少1次: f(i-1,j) and s_i-1 等于 p_j-2
     */

    	if (!p.isEmpty() && p.charAt(0) == '*') {
        	return false;   
    	}

    	boolean[][] f = new boolean[s.length() + 1][p.length() + 1];

    
    	f[0][0] = true;

    

    	// 初始化
    	for (int j = 1; j < p.length(); j+=2) {
        	if (p.charAt(j) == '*') {
        	//j为‘*’，无论是代表0个还是至少一个，后一个的取值都与前一个有关。
            	f[0][j+1] = f[0][j-1];
        	}
    	}

    	for (int i = 1; i <= s.length(); i++) {
        	for (int j = 1; j <= p.length(); j++) {
            	if (p.charAt(j - 1) != '*') {
                	f[i][j] = f[i - 1][j - 1] && isCharMatch(s.charAt(i - 1), p.charAt(j - 1));
            	} else {
                	f[i][j] = f[i][j - 2] || f[i - 1][j] && isCharMatch(s.charAt(i - 1), p.charAt(j - 2));
            	}
        	}
   	 	}

    	return f[s.length()][p.length()];
		}

		// pattern中不存在‘*’
		private boolean isCharMatch(char s, char p) {
    	return p == '.' || s == p;
	}
