# 13. Roman to Integer
## 题目
Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.
## 代码
从尾开始计算，因为涉及到“DC”，“CD”等情况。

	public class Solution {
	    public int romanToInt(String s) {
	        int num=0;
	        for(int i=s.length()-1;i>=0;i--)
	        {
	            char c=s.charAt(i);
	            switch(c)
	            {
            
	                case 'M': num=num+1000;break;        
	                case 'C':num=num+100*(num>=500?-1:1);break;            
	                case 'D':num=num+500;break;
	                case 'X':num=num+10*(num>=50?-1:1);break;           
	                case 'L':num=num+50;break;                   
	                case 'I':num=num+1*(num>=5?-1:1);break;           
	                case 'V':num=num+5;break;            
	            }
	        }
        
	        return num;
	    }
	}
