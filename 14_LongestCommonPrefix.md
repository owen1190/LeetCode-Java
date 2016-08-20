# 14. Longest Common Prefix
## 题目
Write a function to find the longest common prefix string amongst an array of strings.
## 代码
两个String数组比较，得出公共String，再跟下一个String比较

	public class Solution {
	    public String longestCommonPrefix(String[] strs) 
	    {
	        if(strs == null || strs.length == 0)    return "";
	        String pre = strs[0];
	        int i = 1;
	        while(i < strs.length)
	        {
	            while(strs[i].indexOf(pre) != 0)//比较两个String，得出公共String
	                pre = pre.substring(0,pre.length()-1);
	            i++;
	        }   
	        return pre;
	    }
	}


按字符串长度排序，然后比较最短字符串和最长字符串，就能得出公共长度字符串。

	public String longestCommonPrefix(String[] strs) {
	        StringBuilder result = new StringBuilder();
	
	        if (strs!= null && strs.length > 0){

	            Arrays.sort(strs);

	            char [] a = strs[0].toCharArray();
	            char [] b = strs[strs.length-1].toCharArray();
	
	            for (int i = 0; i < a.length; i ++){
	                if (b.length > i && b[i] == a[i]){//字符串中字符相同情况
	                    result.append(b[i]);
	                }
	                else {//字符串中字符不同情况
	                    return result.toString();
	                }
	            }
	        return result.toString();
	    }
