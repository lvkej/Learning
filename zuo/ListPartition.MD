    public static class Node {
		public int value;
		public Node next;

		public Node(int data) {
			this.value = data;
		}
	}

	public static Node listPartition1(Node head,int p) {
		if(head==null) {
			return head;             //先判断是否为零
		}
		Node cur = head;
		int sum=0;
		while(cur!=null) {
			sum++;
			cur=cur.next;
		}
		Node[] n = new Node[sum];        //构造一个数组方便排序
		cur=head;
		for (int i = 0; i < sum; i++) {
			n[i] = cur;
			cur=cur.next;
		}
		arrPartition(n,p);
		for (int i = 0; i < n.length-1; i++) {
			n[i].next=n[i+1];
		}
		n[sum-1].next=null;
		return n[0];
	}


	public static void arrPartition(Node[] n,int p) {
		int less=-1;                //设置小于区、大于区、遍历下标index
		int more =n.length;
		int index = 0;
		while(index<more) {
			if(n[index].value<p) {
				swap(n,++less,index++);
			}else if(n[index].value ==p) {
				index++;
			}else {
				swap(n,--more,index);
			}
		}
	}

	
	public static Node listPartition2(Node head,int p) {
		Node sh = null;
		Node st = null;
		Node eh = null;
		Node et = null;
		Node bh = null;
		Node bt = null;
		Node tem = null;
		while(head!=null) {
			tem=head.next;
			head.next=null;
			if(head.value<p) {
				if(sh==null) {
					sh=head;
					st=head;
				}else {
					st.next=head;
					st=st.next;
				}
			}else if(head.value==p) {
				if(eh==null) {
					eh=head;
					et=head;
				}else {
					et.next=head;
					et=et.next;
				}
			}else  {
				if(bh==null) {
					bh=head;
					bt=head;
				}else {
					bt.next=head;
					bt=bt.next;
				}
			}
			head=tem;
		}
		if(sh!=null) {
			st.next=eh;
			et=eh!=null?et:st;               //若eh为空，则et赋值为st；
			
		}
		if(eh!=null) {
			et.next=bh;
		}
		
		return sh!=null?sh:eh!=null?eh:bh;            //若sh空则eh；若eh空则bh
	}
