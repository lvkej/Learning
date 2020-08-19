//层序遍历


	    	public String serialize(TreeNode root) {
	        if(root==null) {
	        	return "[]";
	        }
	    	String res = "["+root.val;
	        Queue<TreeNode> queue = new LinkedList<TreeNode>();
	        queue.offer(root);
	        while(!queue.isEmpty()) {
	        	TreeNode tmp = queue.poll();
	        	if(tmp.left!=null) {
	        		queue.offer(tmp.left);
	        		res+=","+tmp.left.val;
	        	}else {
	        		res+=",null";
	        	}
	        	if(tmp.right!=null) {
	        		queue.offer(tmp.right);
	        		res+=","+tmp.right.val;
	        	}else {
	        		res+=",null";
	        	}
	        }
	        res+="]";
	        return res;
	    }

	    public TreeNode deserialize(String data) {
	        if(data.equals("[]")) {
	        	return null;
	        }
	        String[] val = data.substring(1, data.length()-1).split(",");
	        int index = 0;
	        TreeNode head = gene(val[index++]);
	        Queue<TreeNode> q = new LinkedList<TreeNode>();
	        q.offer(head);
	        while(!q.isEmpty()) {
	        	TreeNode tmp = q.poll();
	        	tmp.left=gene(val[index++]);
	        	tmp.right=gene(val[index++]);
	        	if(tmp.left!=null) {
	        		q.offer(tmp.left);
	        	}
	        	if(tmp.right!=null) {
	        		q.offer(tmp.right);
	        	}
	        }
	        return head;
	    }
	    
	    public TreeNode gene(String s) {
	    	if(s.equals("null")) {
	    		return null;
	    	}
	    	return new TreeNode(Integer.valueOf(s));
	    }
