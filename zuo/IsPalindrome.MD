    //need n extra space
	  public static boolean isPalindrome1(Node head) {
		boolean res = true;
		Stack<Node> s = new Stack<Node>();
		Node cur = head;
		while(cur!=null) {
			s.push(cur);
			cur=cur.next;
		}
		while(!s.isEmpty()) {
			if(head.value!=s.pop().value) {
				res=false;
				break;
			}
			head=head.next;
		}
		return res;
	}



	//need n/2 extra space
	public static boolean isPalindrome2(Node head) {
		if(head==null||head.next==null) {         //先排除特殊情况！
			return true;
		}
		boolean res = true;
		Node slow = head.next;   //slow赋值为head.next是让结束循环时slow停在一半下一个的位置。
		Node fast = head;     //设置快慢两个指针
		while(fast.next!=null&&fast.next.next!=null) {   //fast.next.next不能越界
			slow=slow.next;
			fast=fast.next.next;
		}
		Stack<Node> s = new Stack<Node>();
		while(slow!=null) {
			s.push(slow);
			slow=slow.next;
		}
		while(!s.isEmpty()) {
			if(s.pop().value!=head.value) {
				res=false;
				break;
			}
			head=head.next;
		}
		return res;
	}
	

	// need 0(1)extra space
	public static boolean isPalindrome3(Node head) {
		if(head==null||head.next==null) {
			return true;
		}
		boolean res=true;
		Node slow = head; //这是让循环结束时slow停在一半前一个，与第二种方式不同
		Node fast = head;
		while(fast.next!=null&&fast.next.next!=null) {
			slow=slow.next;
			fast=fast.next.next;
		}
		
		Node tem = null;               //后一半逆序
		Node n = slow.next;
		slow.next=null;
		while(n!=null) {
			tem=n.next;
			n.next=slow;             //从要逆序的头指针开始
			slow=n;
			n=tem;
		}
		
		n=slow;                       //记录最后一个节点，逆序的头，最后遍历完要恢复原链表
		while(head!=null&&slow!=null) {
			if(head.value!=slow.value) {
				res=false;
				break;
			}
			head=head.next;
			slow=slow.next;
		}
		
		slow=n;     
		n=null;
		while(slow!=null) {          //恢复原链表，从头节点开始，
			tem=slow.next;            //1、记录头节点的next 2、头节点next=n 3、n向前移一位 4、头节点向前移一位
			slow.next=n;
			n=slow;
			slow=tem;
		}
		
		return res;
	}
	
