    public static class Node{
		public int value;
		public Node left;
		public Node right;
		
		public Node(int data) {
			this.value=data;
		}
	}
	
	public static int NodeNum(Node head) {
		if(head==null) {
			return 0;
		}
		return get(head,1,maxheight(head));
	}
	
	public static int get(Node head,int level,int h) { 
		if(level==h) {
			return 1;             //递归结束条件，level=h
		}
		if(maxheight(head.right)+level==h) {
			return (int)Math.pow(2, h-level)+get(head.right,level+1,h);       //h是个常数，表示总高
		}
		else {
			return (int)Math.pow(2, h-level-1)+get(head.left,level+1,h);
		}
	}
	
	public static int maxheight(Node head) {
		if(head==null) {
			return 0;
		}
		int sum=0;
		while(head!=null) {
			head=head.left;
			sum++;
		}
		return sum;
	}
