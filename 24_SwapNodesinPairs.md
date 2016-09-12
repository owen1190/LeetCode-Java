# 24. Swap Nodes in Pairs
## 题目
Given a linked list, swap every two adjacent nodes and return its head.

For example,
Given 1->2->3->4, you should return the list as 2->1->4->3.

Your algorithm should use only constant space. You may not modify the values in the list, only nodes itself can be changed.
## 代码


	public ListNode swapPairs(ListNode head) {
        	ListNode pre=new ListNode(0);
        	pre.next=head;
        	ListNode ln=pre;
        	while(ln.next!=null&&ln.next.next!=null)
        	{
            	ListNode first=ln.next;
           		ListNode second=ln.next.next;
            	first.next=second.next;
            	second.next=first;
            	ln.next=second;
            	ln.next.next=first;
            	ln=ln.next.next;
        	}
        	return pre.next;
    	}
