# 25. Reverse Nodes in k-Group
## 题目
Given a linked list, reverse the nodes of a linked list k at a time and return its modified list.

If the number of nodes is not a multiple of k then left-out nodes in the end should remain as it is.

You may not alter the values in the nodes, only nodes itself may be changed.

Only constant memory is allowed.

For example,
Given this linked list: 1->2->3->4->5

For k = 2, you should return: 2->1->4->3->5

For k = 3, you should return: 3->2->1->4->5
## 代码
先按k值分组，将curr指针移动到k+1位置处，然后组内进行倒置，最终递归。

	public ListNode reverseKGroup(ListNode head, int k) {
        	ListNode curr=head;
        	int count=0;
         	while (curr != null && count != k) { // 移动到 k+1 节点
        		curr = curr.next;
        		count++;
    		}
    		if (count == k) { 
        		curr = reverseKGroup(curr, k); // 头和k节点倒置
        
        		while (count-- > 0) { // 组内倒置 
            		ListNode tmp = head.next;  
            		head.next = curr; 
            		curr = head; 
            		head = tmp; 
        		}
        		head = curr;
    		}
    		return head;
    }
