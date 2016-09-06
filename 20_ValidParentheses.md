# 20. Valid Parentheses
## 题目
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

The brackets must close in the correct order, "()" and "()[]{}" are all valid but "(]" and "([)]" are not.

## 代码
用一个栈存储'('、'['、'{'，一旦遇到另一半时，将栈弹出，相比，如果搭配则为true。最后如果栈中仍有括号，则为假，否则为真。


 	public boolean isValid(String s) {
        	Stack op=new Stack();
        	char[] c=s.toCharArray();
        	for(int i=0;i<c.length;i++)
        	{
           	 	if(c[i]=='('|c[i]=='['|c[i]=='{')
                	op.push(c[i]);
            	else if(c[i]==')'|c[i]==']'|c[i]=='}')
            	{
                	if(op.empty()) return false;
                	char cr= (char)op.pop();
                	if(c[i]==')'&cr!='(') return false;
                	if(c[i]==']'&cr!='[') return false;
                	if(c[i]=='}'&cr!='{') return false;
            	}
            
        	}
        	if(!op.empty()) return false;
        	return true;
    	}

