//递归，非递归
	
	Node head=null,pre=null;							//设置两个全局变量记录首位节点
	public Node treeToDoublyList(Node root) {
        if(root==null) {
        	return root;
        }   
        dfs(root);
        
        head.left=pre;
        pre.right=head;
        return head;
    }
	
	public void dfs(Node root) {
		if(root==null){
			return;
		}
		dfs(root.left);
		
		if(head==null) {								//若head==null表明是首节点，记录
			head = root;				
		}else {
			pre.right=root;
			root.left=pre;			
		}
		pre=root;
		
		dfs(root.right);
	}
	
	public Node treeToDoublyList(Node root) {
        if(root==null) {
        	return root;
        }
        Node head=null,pre=null;
        Node cur = root;
        Stack<Node> s = new Stack<Node>();
        while(cur!=null||!s.isEmpty()) {
        	if(cur!=null) {
        		s.push(cur);
        		cur=cur.left;
        	}else {
        		cur=s.pop();
        		if(head==null) {
        			head=cur;
        			pre=head;
        		}else {
        			pre.right=cur;
        			cur.left=pre;
        			pre=cur;
        		}
        		cur=cur.right;
        	}
        } 
        pre.right=head;
        head.left=pre;
       return head;
    }
	
	ArrayList<Node> list = new ArrayList<Node>();
	public Node treeToDoublyList(Node root) {
        if(root==null) {
        	return root;
        }
        Node cur = root;
        Stack<Node> s = new Stack<Node>();
        while(cur!=null||!s.isEmpty()) {
        	if(cur!=null) {
        		s.push(cur);
        		cur=cur.left;
        	}else {
        		list.add(s.peek());
        		cur=s.pop().right;
        	}
        }       
       
        for (int i = 0; i < list.size(); i++) {
			list.get(i).left=list.get(preint(i));
			list.get(i).right=list.get(nextint(i));
		}
        return list.get(0);
    }
	
	public int nextint(int i) {
		return i==list.size()-1 ? 0: i+1;
	}
	
	public int preint(int i) {
		return i==0 ? list.size()-1 : i-1;
	}
