# 19. Remove Nth Node From End of List
## 题目
Given a linked list, remove the nth node from the end of list and return its head.

For example,

   Given linked list: 1->2->3->4->5, and n = 2.

   After removing the second node from the end, the linked list becomes 1->2->3->5.
## 代码
通过front和behind间隔出n+1个距离，然后同时向后移动，直到front到达结束处，开始删除结点


	public ListNode removeNthFromEnd(ListNode head, int n) {
	        ListNode start = new ListNode(0);
	        ListNode front=start,behind=start;
	        behind.next=head;
	        for(int i=1;i<=n+1;i++)
	        {
	            front=front.next;
	        }
	        while(front!=null)
	        {
	            behind=behind.next;
	            front=front.next;
	        }
	        behind.next=behind.next.next;
	        return start.next;
	    }
