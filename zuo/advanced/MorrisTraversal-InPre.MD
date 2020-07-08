    public static class Node{
		public int value;
		Node left;
		Node right;
		public Node(int value) {
			this.value = value;
		}
	}
	
	public static void process(Node head) {		//递归遍历
		if(head==null) {
			return;
		}		
//		System.out.println(head.value); 前序
		process(head.left);
//		System.out.println(head.value); 中序
		process(head.right);
//		System.out.println(head.value); 后序
	}
	
	public static void MorrisIn(Node head) {
		if(head==null) {
			return ;
		}
		Node cur1 = head;
		Node cur2 = null;
		
		while(cur1!=null) {			//循环条件
			cur2=cur1.left;
			
			if(cur2!=null) {		//先判断cur1是否有左儿子
				while(cur2.right!=null&&cur2.right!=cur1) {		//找cur2最右边的儿子。
					cur2=cur2.right;
				}
				if(cur2.right==null) {				//若cur2右儿子为空，cur2.right=cur1; cur1=cur1.left
					cur2.right=cur1;
					cur1=cur1.left;
					continue;
				}else {							//else情况就是cur2右儿子为cur1;cur2.right=null;cur1=cur1.right
					cur2.right=null;
					
				}
			}
			
			System.out.print(cur1.value + " ");	//中序遍历，再cur右移之前print
			cur1=cur1.right;		//若cur1没左儿子，cur1=cur1.right
		}
		System.out.println();
		
	}
	
	public static void Morrispre(Node head) {
		if(head==null) {
			return ;
		}
		Node cur1 = head;
		Node cur2 = null;
		
		while(cur1!=null) {			//循环条件
			cur2=cur1.left;
			
			if(cur2!=null) {		//先判断cur1是否有左儿子
				while(cur2.right!=null&&cur2.right!=cur1) {		//找cur2最右边的儿子。
					cur2=cur2.right;
				}
				if(cur2.right==null) {				//若cur2右儿子为空，cur2.right=cur1; cur1=cur1.left
					cur2.right=cur1;
					System.out.print(cur1.value + " ");	//先序遍历，在左移之前。
					cur1=cur1.left;
					continue;
				}else {							//else情况就是cur2右儿子为cur1;cur2.right=null;cur1=cur1.right
					cur2.right=null;
					
				}
			}else {
				System.out.print(cur1.value + " ");	//这个else对应的是没有左儿子的cur1，
			}
			
			cur1=cur1.right;		//若cur1没左儿子，cur1=cur1.right
		}
		System.out.println();
		
	}
