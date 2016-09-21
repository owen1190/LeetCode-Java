# 29. Divide Two Integers
## 题目
Divide two integers without using multiplication, division and mod operator.

If it is overflow, return MAX_INT.
## 代码
将除数累加的思想，但是累加通过位运算方法实现。
例如15/3，将3右移一位变成6,6右移一位变成12，以此类推，到24时，已经大于15，而这其中由3变成12运行两次位运算，四次累加。而最后还有15-12=3，再循环，最终计算出需要五次累加。


 	public int divide(int dividend, int divisor) 
    	{
        	//除数为0或被除数为最小值，除数为-1时，返回的为最大值。
        	if(divisor==0||(dividend==Integer.MIN_VALUE&&divisor==-1)) return Integer.MAX_VALUE;
        	int sign=((dividend<0)^(divisor<0))? -1:1;
        	long divd=Math.abs((long)dividend);
        	long divs=Math.abs((long)divisor);
        	int ans=0;
        	while(divd>=divs)
        	{
            	long temp=divs,count=1;
            	while((temp<<1)<=divd)
            	{
                	temp<<=1;
                	count<<=1;
            	}
            	divd-=temp;
            	ans+=count;            
        	}
        	return sign == 1 ? ans : -ans; 
    	}
