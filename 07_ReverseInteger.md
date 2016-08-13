# 7. Reverse Integer
## 题目
Reverse digits of an integer.

Example1: x = 123, return 321
Example2: x = -123, return -321
## 代码

	public class Solution {
    	public int reverse(int x) {
        	long r = 0;
        	while(x != 0){
            	r = r*10 + x%10;
            	x /= 10;
        	}
        	if(r >= Integer.MIN_VALUE && r <= Integer.MAX_VALUE)
            	return (int)r;
        	else
            	return 0;
    	}
	}
