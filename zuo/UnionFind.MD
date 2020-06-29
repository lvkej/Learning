    public static class Node {
		// whatever you like
	}

	public static class UnionFindSet {
		public HashMap<Node, Node> fatherMap;
		public HashMap<Node, Integer> sizeMap;

		public UnionFindSet() {
			fatherMap = new HashMap<Node, Node>();
			sizeMap = new HashMap<Node, Integer>();
		}

		public void makeSets(List<Node> nodes) {
			fatherMap.clear();
			sizeMap.clear();
			for (Node node : nodes) {
				fatherMap.put(node, node);
				sizeMap.put(node, 1);
			}
		}

		//递归
		public Node findHead1(Node node) {
			Node father = fatherMap.get(node);
			if(father!=node) {
				father = fatherMap.get(father);
			}
			fatherMap.put(node,father);					//优化，扁平化，node上面的所有节点都单独指向father
			return father;
		}
		//非递归
		public Node findHead2(Node node) {
			Stack<Node> s = new Stack<Node>();
			Node cur=node;
			Node father=fatherMap.get(cur);
			while(father!=cur) {
				s.push(cur);
				cur=father;
				father=fatherMap.get(cur);
			}
			while(!s.isEmpty()) {
				fatherMap.put(s.pop(),father); //栈储存元素
			}
			return father;
		}
		
		public boolean isSameSet(Node a,Node b) {
			return findHead1(b)==findHead1(a);
			
		}
		public void union(Node a,Node b) {
			if(a==null||b==null) {
				return;
			}
			Node head1=findHead1(a);
			Node head2=findHead1(b);
			if(head1!=head2) {
				int sizea=sizeMap.get(head1);
				int sizeb=sizeMap.get(head2);
				if(sizea<=sizeb) {
					fatherMap.put(head1, head2);
					sizeMap.put(head2, sizea+sizeb);			//对head节点进行size操作，只需改变head的size
				}else {
					fatherMap.put(head2,head1);
					sizeMap.put(head1, sizea+sizeb);
				}
			}
		}
