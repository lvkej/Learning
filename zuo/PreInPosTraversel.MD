    public static class Node{
		public int value;
		public Node left;
		public Node right;
		
		public Node(int data){
			this.value=data;
		}
	}
	

	public static void preOrderRecur(Node head) {
		if(head==null) {
			return ;               //返回条件，head==null；
		}
		System.out.print(head.value+" ");
		preOrderRecur(head.left);
		preOrderRecur(head.right);
		
	}


	
	public static void inOrderRecur(Node head) {
		if (head == null) {
			return;
		}
		inOrderRecur(head.left);
		System.out.print(head.value + " ");
		inOrderRecur(head.right);
	}

	public static void posOrderRecur(Node head) {
		if (head == null) {
			return;
		}
		posOrderRecur(head.left);
		posOrderRecur(head.right);
		System.out.print(head.value + " ");
	}

	
	//非递归
	public static void preOrderUnRecur(Node head) {
		System.out.print("pre-order: ");
		Stack<Node> s = new Stack<Node>();
		if(head!=null) {
			s.push(head);
			while(!s.isEmpty()) {
				head=s.pop();
				System.out.print(head.value+" ");
				if(head.right!=null) {
					s.add(head.right);
				}
				if(head.left!=null) {
					s.push(head.left);
				}
			}
		}
		System.out.println();
	}


	public static void inOrderUnRecur(Node head) {
		System.out.print("in-order: ");
		if(head!=null) {
			Stack<Node> s = new Stack<Node>();
			while(!s.isEmpty()||head!=null) {
				if(head!=null) {
					s.push(head);
					head=head.left;                  //先将左半边全部压入栈
				}
				else {
					head=s.pop();
					System.out.print(head.value + " ");
					head=head.right;
				}
			}
		}
		System.out.println();
	}


	public static void posOrderUnRecur1(Node head) { //左右中逆序就是中右左，考虑用栈实现逆序。
		System.out.print("pos-order: ");
		if(head!=null) {
			Stack<Node> s1 = new Stack<Node>();
			Stack<Node> s2 = new Stack<Node>();
			s1.push(head);
			while(!s1.isEmpty()) {
				head=s1.pop();
				s2.push(head);
				if(head.left!=null) {
					s1.push(head.left);
				}
				if(head.right!=null) {
					s1.push(head.right);
				}				
			}
			while (!s2.isEmpty()) {
				System.out.print(s2.pop().value + " ");
			}
		}
		System.out.println();
	}
	
	//层序遍历
	public List<List<Integer>> levelOrder(TreeNode root) {        
        List<List<Integer>> res = new ArrayList<>();
        if(root==null){
            return res;
        }
        Deque<TreeNode> deque = new LinkedList<>();
        deque.addLast(root);
        while (!deque.isEmpty()) {
            int size = deque.size();
            List<Integer> list = new ArrayList<>();
            while (size>0){
                TreeNode node = deque.pollFirst();
                list.add(node.val);
                if(node.left!=null){
                    deque.addLast(node.left);
                }
                if(node.right!=null){
                    deque.addLast(node.right);
                }
                size--;
            }
            res.add(list);
        }
        return res;
    }
