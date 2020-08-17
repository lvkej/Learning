    public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
        ListNode head= new ListNode(0);
        ListNode tmp=head;
        
        while(l1!=null&&l2!=null){
            if(l1.val<l2.val){
                head.next=l1;
                l1=l1.next;
                head=head.next;
            }else{
                head.next = l2;
                l2=l2.next;
                head=head.next;
            }

        }
        head.next= l1!=null ? l1 : l2;
        head=tmp.next;
        return head;
    }

		//递归
        public ListNode mergeTwoLists(ListNode l1, ListNode l2){
		if(l1 == null) return l2;
		if(l2 == null) return l1;
		if(l1.val < l2.val){
			l1.next = mergeTwoLists(l1.next, l2);
			return l1;
		} else{
			l2.next = mergeTwoLists(l1, l2.next);
			return l2;
		}
        }
