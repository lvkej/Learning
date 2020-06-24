    public static class Node {
		public int value;
		public Node left;
		public Node right;

		public Node(int data) {
			this.value = data;
		}
	}

	public static class returndata{
		int height;
		boolean isb;
		public returndata(int height, boolean isb) {
			this.height = height;
			this.isb = isb;
		}
		
	}
	
	
	public static returndata process(Node head) {
		if(head==null) {
			return new returndata(0, true);          //首先确认递归结束条件！！
		}
		returndata left = process(head.left);        //调用下一级直至结束条件
		if(!left.isb) {
			return new returndata(0, false);              //中间是各种可能性
		}
		returndata right = process(head.right);
		if(!right.isb) {
			return new returndata(0, false);
		}
		if(Math.abs(left.height-right.height)>1) {
			return new returndata(0, false);
		}
		return new returndata(Math.max(left.height, right.height), true); //最后确认返回给上级的结果！！
	}
