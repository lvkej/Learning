    public static class Node {
		public int value;
		public Node next;

		public Node(int data) {
			this.value = data;
		}
	}

	public static Node josephusKill1(Node head, int m) {
		if (head == null || head.next == head || m < 1) {
			return head;
		}
		Node last = head;
		while (last.next != head) {
			last = last.next;
		}
		int count = 0;
		while (head != last) {
			if (++count == m) {
				last.next = head.next;
				count = 0;
			} else {
				last = last.next;
			}
			head = last.next;
		}
		return head;
	}

	public static Node josephusKill(Node head, int m) {
		if(head==null||head.next==head||m<1) {
			return head;
		}
		int size=1;
		Node cur=head;
		while(cur.next!=head) {
			size++;
			cur=cur.next;
		}
		int tem = get(size,m);
		while(--tem>0) {
			head=head.next;
		}
		head.next=head;
		return head;
	}
	
	public static int get(int size, int m) {				//s=(m-1)%size+1
		if(size==1) {										//旧 = (新-1+s)%size+1
			return 1;
		}
		return (get(size-1,m)+m-1)%size+1;					//老坐标与新坐标的关系
	}
	//通过画图推算出旧坐标和新坐标的关系，递归得到最后剩余坐标最开始的坐标
