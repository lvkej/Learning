    public static class Node {
		public int value;
		public Node left;
		public Node right;

		public Node(int data) {
			this.value = data;
		}
	}

	public static Node biggestSubBST(Node head) {
		int[] record = new int[3]; // 0->size, 1->min, 2->max
		return posOrder(head, record);
	}
	
	public static class ReturnType{
		public int size;
		public Node head;
		public int min;
		public int max;
		
		public ReturnType(int a, Node b,int c,int d) {
			this.size =a;
			this.head = b;
			this.min = c;
			this.max = d;
		}
	}
	
	public static ReturnType process(Node head) {
		if(head == null) {
			return new ReturnType(0,null,Integer.MAX_VALUE, Integer.MIN_VALUE);
		}
		Node left = head.left;
		ReturnType leftSubTressInfo = process(left);
		Node right = head.right;
		ReturnType rightSubTressInfo = process(right);
		
		int includeItSelf = 0;
		if(leftSubTressInfo.head == left 
				&&rightSubTressInfo.head == right
				&& head.value > leftSubTressInfo.max
				&& head.value < rightSubTressInfo.min
				) {
			includeItSelf = leftSubTressInfo.size + 1 + rightSubTressInfo.size;
		}
		int p1 = leftSubTressInfo.size;
		int p2 = rightSubTressInfo.size;
		int maxSize = Math.max(Math.max(p1, p2), includeItSelf);
		
		Node maxHead = p1 > p2 ? leftSubTressInfo.head : rightSubTressInfo.head;
		if(maxSize == includeItSelf) {
			maxHead = head;
		}
		
		return new ReturnType(maxSize,
				maxHead, 
				Math.min(Math.min(leftSubTressInfo.min,rightSubTressInfo.min),head.value),
				Math.max(Math.max(leftSubTressInfo.max,rightSubTressInfo.max),head.value));	
	}
