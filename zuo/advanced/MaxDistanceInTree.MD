    public static class Node {
		public int value;
		public Node left;
		public Node right;

		public Node(int data) {
			this.value = data;
		}
	}

	public static int maxDistance(Node head) {
		int[] record = new int[1];
		return posOrder(head, record);
	}
	
	public static class ReturnType{
		public int maxDistance;
		public int h;
		
		public ReturnType(int m, int h) {
			this.maxDistance = m;;
			this.h = h;
		}
	}
	
	public static ReturnType process(Node head) {
		if(head == null) {
			return new ReturnType(0,0);
		}
		ReturnType leftReturnType = process(head.left);			//第一种可能，左子树的最大
		ReturnType rightReturnType = process(head.right);		//第二种可能，右子树的最大
		int includeHeadDistance = leftReturnType.h + 1 + rightReturnType.h;		//第三种可能，通过head节点，左右相加
		int p1 = leftReturnType.maxDistance;
		int p2 = rightReturnType.maxDistance;
		int resultDistance = Math.max(Math.max(p1, p2), includeHeadDistance);
		int hitself  = Math.max(leftReturnType.h, leftReturnType.h) + 1;
		return new ReturnType(resultDistance, hitself);
	}
