    public class ListNode{
	    int val;
	    ListNode next;
	    ListNode(int x){
	        val = x;
	    }
	}
	
    public ListNode deleteNode(ListNode head, int val) {
    if(head==null){
        return null;
    }
    ListNode cur = head;
    ListNode newnode = head.next;
    if(head.val==val){            
        head.next = null;
        return newnode;
    }

    while(newnode.val!=val){
        cur=newnode;
        newnode=newnode.next;

    }

    cur.next=newnode.next;
    return head;
}
