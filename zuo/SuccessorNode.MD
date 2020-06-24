    public static class Node {
		public int value;
		public Node left;
		public Node right;
		public Node parent;

		public Node(int data) {
			this.value = data;
		}
	}

	public static Node getSuccessorNode(Node node) {
		if(node==null) {
			return null;         //特殊情况
		}
		if(node.right!=null) {
			return getLeftMost(node);             //有右儿子时，后继节点是右孩子中最左的节点
		}else {
			Node parent=node.parent;
			while(parent!=null&&parent.left!=node) { //没右儿子时，当父结点的左儿子是node时为后继节点。
				node=parent;
				parent=node.parent;
			}
			return parent;
		}
	}
	public static Node getLeftMost(Node node) {
		Node n = node.right;
		while(n.left!=null) {
			n=n.left;
		}
		return n;
		
	}
