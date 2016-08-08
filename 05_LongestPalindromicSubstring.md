# 5. Longest Palindromic Substring

## 题目
Given a string S, find the longest palindromic substring in S. You may assume that the maximum length of S is 1000, and there exists one unique longest palindromic substring.

## 代码

采用中心扩展法，把每个字符当成中心，比较左边和右边的。如果为奇数，则比较i-1和i+1，如果为偶数，则比较i和i+1


	public String longestPalindrome(String s) {
       int N=s.length();
       int max=0;
       int lo=0;
       if(N==1) return s;
       for(int i=0;i<N;i++)//奇数情况
       {
           int j=i-1,k=i+1;
           while(j>=0&&k<N&&s.charAt(j)==s.charAt(k))
           {
               if(k-j+1>max)
               {
                   max=k-j+1;
                   lo=j;
               }
               j--;
               k++;
           }
       }
       for(int i=0;i<N;i++)//偶数奇数
       {
           int j=i,k=i+1;
           while(j>=0&&k<N&&s.charAt(j)==s.charAt(k))
           {
               if(k-j+1>max)
               {
                   max=k-j+1;
                   lo=j;
               }
               j--;
               k++;
           }
       }
       if(max>0)
           {return s.substring(lo,lo+max);}
       else return null;
    }


DP解法：
如果s[i][j]为回文子串，则s[i+1][j-1]一定为回文子串


	public String longestPalindrome(String s) 
	{
  		int n = s.length();
 		String res = null;
 		boolean[][] dp = new boolean[n][n];   
  		for (int i = n - 1; i >= 0; i--) 
		{
    		for (int j = i; j < n; j++) 
			{
      			dp[i][j] = s.charAt(i) == s.charAt(j) && (j - i < 3 || dp[i + 1][j - 1]);
            
      			if (dp[i][j] && (res == null || j - i + 1 > res.length())) 
				{
        			res = s.substring(i, j + 1);
      			}
    		}
  		}    
  		return res;
	}
