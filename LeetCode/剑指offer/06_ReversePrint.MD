    public int[] reversePrint(ListNode head) {
		if(head==null) {
			return new int[0];
		}
		
		ListNode tail = head;
		int total=1;
		while(tail.next!=null) {
			total++;
			tail = tail.next;
		}
		
		ListNode cur = head;
		ListNode next = head.next;
		ListNode tem = null;
		while(next!=null) {
			next = cur.next;
			cur.next = tem;
			tem = cur;
			cur=next;
		}
		
		int[] res = new int[total];
		int index = 0;
		while(tail!=null) {
			res[index++] = tail.val;
			tail=tail.next;
		}
		 
		return res;
		 
	}
