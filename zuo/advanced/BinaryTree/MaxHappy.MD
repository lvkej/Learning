    public static class Node{
		public int value;
		public ArrayList<Node> next;
		public Node(int value){
			this.value = value;
			this.next = new ArrayList<Node>();
		}
	}
	
	public static class returndata{
		public int come;		
		public int income;
		public returndata(int come,int income) {
			this.come = come;
			this.income = income;
		}
	}

	public static int getmax(Node head) {
		returndata res = process(head);
		return Math.max(res.come, res.income);
	}
	
	public static returndata process(Node head) {
		int come = head.value;
		int income = 0;
		
		for(Node each:head.next) {
			returndata next = process(each);
			income+=Math.max(next.come, next.income);		//不来的话取下一级中较大的值
			come+=next.income;								//来的话加下一级中不来的值
		}
		
		return new returndata(come,income);
	}
	
