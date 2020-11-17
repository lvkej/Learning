
>双指针，快慢指针，一次遍历，注意只有一个节点的特殊情况
```
public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode slow=head,fast=head,pre=head;
        while(n>0){
            fast=fast.next;
            n--;
        }

        while(fast!=null){
            pre=slow;
            slow=slow.next;
            fast=fast.next;
        }
        if(pre==slow){
            return slow.next;
        }
        /*当链表长度为1时，特殊情况，返回null*/
        pre.next=slow.next;
        return head;

    }
```
