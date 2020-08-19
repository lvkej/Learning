  LinkedList<LinkedList<Integer>> res = new LinkedList<LinkedList<Integer>>();
	LinkedList<Integer> tmp = new LinkedList<Integer>();
	
  public LinkedList<LinkedList<Integer>> pathSum(TreeNode root, int sum) {
    	recur(root,sum);
    	return res;
    }
	
	public void recur(TreeNode root,int sum) {
		if(root==null) {
			return;
		}
		tmp.add(root.val);
		sum-=root.val;
		if(sum==0&&root.left==null&&root.right==null){
			res.add(new LinkedList(tmp));
		}
		recur(root.left,sum);
		recur(root.right,sum);
		tmp.removeLast();							//tmp removelast 就可以用一个tmp遍历所有node
	}
