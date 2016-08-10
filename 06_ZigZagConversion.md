# 6. ZigZag Conversion
## 题目
The string "PAYPALISHIRING" is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R
And then read line by line: "PAHNAPLSIIGYIR"
## 代码
n=numRows
Δ=2n-2    1                           2n-1                         4n-3
Δ=        2                     2n-2  2n                    4n-4   4n-2
Δ=        3               2n-3        2n+1              4n-5       .
Δ=        .           .               .               .            .
Δ=        .       n+2                 .           3n               .
Δ=        n-1 n+1                     3n-3    3n-1                 5n-5
Δ=2n-2    n                           3n-2                         5n-4

cycle就是1和2n-1之间的差值。而第二行的第二个数是2n-1减1，第三行的第二个数是2n-1减2....所以第n-1行的第二个数就是2n-1-(n-1)。而且除了第一行和最后一行没有中间的数之外，其余都有，而且每个数之间差的就是一个cycle。
	 
	
		public String convert(String s, int numRows) 
		{
    		if (numRows < 2) 
			{
        		return s;
    		}    
    		StringBuilder answer = new StringBuilder();
    		int cycle = 2*numRows-2;
    		for (int k=0; k < numRows; k++) 
			{
        		for (int i=k, j=cycle-k; i < s.length(); i+=cycle, j+=cycle) 
				{
        	    	answer.append(s.charAt(i));					
            		if (k !=0 && k != numRows-1 && j < s.length()) 	answer.append(s.charAt(j));
        		}
    		}
    		return answer.toString();
		}

