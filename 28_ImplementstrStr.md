# 28. Implement strStr()

## 题目
Implement strStr().

Returns the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
## 代码
第一种方法

	public int strStr(String haystack, String needle) {
  		for (int i = 0; ; i++) {
    		for (int j = 0; ; j++) {
      			if (j == needle.length()) return i;
      			if (i + j == haystack.length()) return -1;
      			if (needle.charAt(j) != haystack.charAt(i + j)) break;
    		}
  		}
	}


第二种方法直接通过String的api

	public int strStr(String haystack, String needle) 
	{
    	return haystack.indexOf(needle);
	}
