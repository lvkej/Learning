    public static class Node {
		public int value;
		public Node next;

		public Node(int data) {
			this.value = data;
		}
	}
	
	//需要新建hashmap表，额外空间
	public static Node getIntersectNode2(Node head1,Node head2) {
		HashSet<Node> set = new HashSet<Node>();
		if(head1== null||head2==null) {
			return null;
		}
		Node cur1=head1;
		while(cur1!=null&&!set.contains(cur1)) {
			set.add(cur1);
			cur1=cur1.next;
		}
		Node cur2=head2;
		int cnt2=getlength(head2);
		while(cnt2>0) {
			if(set.contains(cur2)) {
				return cur2;
			}else {
				set.add(cur2);
				cur2=cur2.next;
			}
		}
		return null;
	}
	
	public static int getlength(Node head) {
		HashSet<Node> set = new HashSet<Node>();
		Node cur = head;
		int cnt = 0;
		while(cur!=null&&!set.contains(cur)) {
			set.add(cur);
			cnt++;
			cur=cur.next;
		}
		return cnt;
	}

	//不需要额外空间
	
	public static Node getIntersectNode(Node head1,Node head2) {
		if(head1==null||head2==null) {      //先排除特殊情况
			return null;
		}
		Node loop1 = getLoopNode(head1);
		Node loop2 = getLoopNode(head2);
		if(loop1==null&&loop2==null) {
			return noLoop(head1,head2);
		}
		if(loop1!=null&&loop2!=null) {
			return bothLoop(head1,loop1,head2,loop2);
		}
		return null;
	}

	public static Node getLoopNode(Node head) {
		if(head==null||head.next==null||head.next.next==null) {
			return null;                                        //特殊情况
		}
		Node slow=head.next;
		Node fast = head.next.next;
		while(slow!=fast) {
			if(fast.next==null||fast.next.next==null) {
				return null;
			}
			fast=fast.next.next;
			slow=slow.next;
		}
		fast=head;
		while(slow!=fast) {
			fast=fast.next;
			slow=slow.next;
		}
		return fast;
	}
	
	


	public static Node noLoop(Node head1,Node head2) {
		if(head1== null||head2==null) {
			return null;
		}
		Node cur1=head1;
		Node cur2=head2;
		int cnt=0;
		while(cur1.next!=null) {
			cnt++;                     //只需要差值，可以省一个变量
			cur1=cur1.next;
		}
		while(cur2.next!=null) {
			cnt--;
			cur2=cur2.next;
		}
		if(cur1!=cur2) {
			return null;
		}	
		cur1= cnt>0?head1:head2;        //cur1赋值为较长的链表
		cur2= cur1==head1?head2:head1;
		cnt=Math.abs(cnt);
		while(cnt>0) {
			cur1=cur1.next;
			cnt--;
		}
		while(cur1!=cur2) {
			cur1=cur1.next;
			cur2=cur2.next;
		}
		return cur1;		
		
	}
