    public static class Node {
		public int value;
		public Node left;
		public Node right;

		public Node(int data) {
			this.value = data;
		}
	}

	public static void printTree(Node head) {
		System.out.println("Binary Tree:");
		printInOrder(head, 0, "H", 17);
		System.out.println();
	}

	public static void printInOrder(Node head,int height,String to,int len) {
		if(head==null) {
			return;
		}
		printInOrder(head.right, height+1, "v", len);  //递归右儿子直至空
		//构造字符串val 空格+内容+空格
		String val =to+head.value+to;
		int lenm=val.length();
		int lenl=(len-lenm)/2;
		int lenr=len-lenm-lenl;
		val=getSpace(lenl)+val+getSpace(lenr);
		
		System.out.println(getSpace(height*len)+val);
		printInOrder(head.left, height+1, "^", len);
	}

	
	public static String getSpace(int num) {
		StringBuffer sb = new StringBuffer();
		for (int i = 0; i < num; i++) {
			sb.append(" ");
		}
		return sb.toString();//转化为字符串
	}

