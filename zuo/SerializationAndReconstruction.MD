    public static class Node {
		public int value;
		public Node left;
		public Node right;

		public Node(int data) {
			this.value = data;
		}
	}

	public static String serialByPre(Node head) {
		if(head==null) {
			return "#!";
		}
		String res = head.value+"!";
		res+=serialByLevel(head.left);
		res+=serialByLevel(head.right);
		return res;
	}
	
	public static Node reconByPreString(String ps) {
		String[] values = ps.split("!");
		Queue<String> q = new LinkedList<String>();
		for (int i = 0; i < values.length; i++) {
			q.offer(values[i]);
		}
		return reconPreOrder(q);
	}
	
	public static Node reconPreOrder(Queue<String> q) {
		String v = q.poll();
		if(v.equals("#")) {
			return null;
		}
		Node head = new Node(Integer.valueOf(v));
		head.left=reconPreOrder(q);
		head.right=reconPreOrder(q);     //递归
		return head;
	}




	public static String serialByLevel(Node head) {
		if (head == null) {
			return "#!";
		}
		String res = head.value + "!";
		Queue<Node> queue = new LinkedList<Node>();            //层序遍历用queue，非递归。
		queue.offer(head);
		while (!queue.isEmpty()) {
			head = queue.poll();
			if (head.left != null) {
				res += head.left.value + "!";
				queue.offer(head.left);
			} else {
				res += "#!";
			}
			if (head.right != null) {
				res += head.right.value + "!";
				queue.offer(head.right);
			} else {
				res += "#!";
			}
		}
		return res;
	}

	public static Node reconByLevelString(String levelStr) {
		String[] values = levelStr.split("!");
		int index = 0;
		Node head = generateNodeByString(values[index++]);
		Queue<Node> queue = new LinkedList<Node>();
		if (head != null) {
			queue.offer(head);
		}
		Node node = null;
		while (!queue.isEmpty()) {
			node = queue.poll();
			node.left = generateNodeByString(values[index++]);
			node.right = generateNodeByString(values[index++]);
			if (node.left != null) {
				queue.offer(node.left);
			}
			if (node.right != null) {
				queue.offer(node.right);
			}
		}
		return head;
	}

	public static Node generateNodeByString(String val) {
		if (val.equals("#")) {
			return null;
		}
		return new Node(Integer.valueOf(val));
	}
