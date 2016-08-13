# 8. String to Integer (atoi)

## 题目
Implement atoi to convert a string to an integer.

Hint: Carefully consider all possible input cases. If you want a challenge, please do not see below and ask yourself what are the possible input cases.

Notes: It is intended for this problem to be specified vaguely (ie, no given input specs). You are responsible to gather all the input requirements up front.
## 代码

	
    	public int myAtoi(String str) 
		{
    		int index = 0, sign = 1, total = 0;
    	//字符串为空
    		if(str.length() == 0) return 0;

    	//跳过空格
    		while(str.charAt(index) == ' ' && index < str.length())
        		index ++;

    	//存储正负号
    		if(str.charAt(index) == '+' || str.charAt(index) == '-')
			{
        		sign = str.charAt(index) == '+' ? 1 : -1;
        		index ++;
    		}

    	//4. Convert number and avoid overflow
    		while(index < str.length())
			{
        		int digit = str.charAt(index) - '0';
        		if(digit < 0 || digit > 9) break;

        		//check if total will be overflow after 10 times and add digit
        		if(Integer.MAX_VALUE/10 < total || Integer.MAX_VALUE/10 == total && Integer.MAX_VALUE %10 < digit)
            		return sign == 1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;

        		total = 10 * total + digit;
        		index ++;
    		}
    		return total * sign;
		}
	
