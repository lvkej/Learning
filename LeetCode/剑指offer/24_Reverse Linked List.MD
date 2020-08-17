    class Solution {
    public ListNode reverseList(ListNode head) {
        if(head==null){
            return null;
        }
        ListNode cur = head;
        ListNode tmp = null;

        while(cur.next!=null){
            ListNode next = cur.next;
            cur.next = tmp;
            tmp=cur;
            cur=next;
        }
        cur.next = tmp;
        return cur;
        
    }
}
