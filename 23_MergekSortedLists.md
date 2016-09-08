# 23. Merge k Sorted Lists
## 题目 
Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.
## 代码
先将lists数组切分为两部分，然后再归并

	public ListNode mergeKLists(ListNode[] lists) {
    	   return partion(lists,0,lists.length-1);
    	}
		//切分运算
    	public ListNode partion(ListNode[] lists,int i,int j)
    	{
    	    if(i==j) return lists[i];
    	    if(i<j)
    	    {
    	        int r=(i+j)/2;
    	        ListNode l1=partion(lists,i,r);
    	        ListNode l2=partion(lists,r+1,j);
    	        return merge(l1,l2);
    	    }
    	    else return null;
    	}
		//合并运算
    	public ListNode merge(ListNode l1,ListNode l2)
    	{
    	    if(l1==null) return l2;
    	    if(l2==null) return l1;
    	    ListNode l3;
    	    if(l1.val < l2.val)
    	     {
    	        l3 = l1;
    	        l3.next = merge(l1.next, l2);
    	    }
    	    else
    	    {
    	        l3 = l2;
    	        l3.next = merge(l1, l2.next);
    	    }
    	    return l3;
    	}
