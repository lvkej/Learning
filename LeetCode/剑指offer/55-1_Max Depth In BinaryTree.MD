    int res;
	public int maxDepth(TreeNode root) {
		if(root==null) {
			return 0;
		}
		int level=1;
		dfs(root,level);
		return res;
    }
	
	public void dfs(TreeNode root,int level) {
		if(root.left==null&&root.right==null) {
			res=Math.max(level, res);
			return;
		}
		if(root.left!=null) {
			dfs(root.left,level+1);
		}
		if(root.right!=null) {
			dfs(root.right,level+1);
		}
	}
  
  //递归
      public int maxDepth(TreeNode root) {
		if(root==null) {
			return 0;
		}
		return Math.max(maxDepth(root.left),maxDepth(root.right))+1;
    }
