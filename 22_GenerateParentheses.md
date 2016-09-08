# 22. Generate Parentheses
## 题目
Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.

For example, given n = 3, a solution set is:


	[
  	"((()))",
 	"(()())",
  	"(())()",
  	"()(())",
  	"()()()"
	]


## 代码

	public List<String> generateParenthesis(int n) {
       List<String> list = new ArrayList<>();
       generate(list,"",0,0,n);
       return list;
    }
    public void generate(List<String> list,String str,int begin,int end,int n)
    {
        if(str.length()==n*2)
        {
            list.add(str);
            return;
        }
        //小于n，添加左括号。
		if(begin<n) generate(list,str+"(",begin+1,end,n);        
		if(begin>end) generate(list,str+")",begin,end+1,n);
    }

