    public static class Node {
		public int p;
		public int c;

		public Node(int p, int c) {
			this.p = p;
			this.c = c;
		}
	}

	public static class MinCostComparator implements Comparator<Node> {

		@Override
		public int compare(Node o1, Node o2) {
			return o1.c - o2.c;
		}

	}

	public static class MaxProfitComparator implements Comparator<Node> {

		@Override
		public int compare(Node o1, Node o2) {
			return o2.p - o1.p;
		}

	}

	public static int findMaximizedCapital(int k, int W, int[] Profits, int[] Capital) {
		Node[] nodes = new Node[Profits.length];
		for (int i = 0; i < nodes.length; i++) {
			nodes[i] = new Node(Profits[i],Capital[i]);
		}
		PriorityQueue<Node> mincostq = new PriorityQueue<Node>(new MinCostComparator());
		PriorityQueue<Node> maxproq = new PriorityQueue<Node>(new MaxProfitComparator());
		for (int i = 0; i < nodes.length; i++) {
			mincostq.add(nodes[i]);
		}
		for (int i = 0; i < nodes.length; i++) {
			while(!mincostq.isEmpty()&&mincostq.peek().c<=W) {
				maxproq.add(mincostq.poll());
			}
			if(maxproq.isEmpty()) {
				return W;
			}
			W+=maxproq.poll().p;
		}
		return W;

	}
