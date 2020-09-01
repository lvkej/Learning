    public boolean isBalanced(TreeNode root) {
		if(root==null) {
			return true;
		}
		int lefth = getheight(root.left);
		int righth = getheight(root.right);
		if(Math.abs(lefth-righth)>1) {
			return false;
		}
		
		return isBalanced(root.left)&&isBalanced(root.right);
    }
	
	public int getheight(TreeNode root) {
		if(root==null) {
			return 0;
		}
		return Math.max(getheight(root.left), getheight(root.right))+1;
	}
	
	//从下往上计算，O(N)
	
	public boolean isBalanced(TreeNode root) {
		return recur(root)!=-1;
    }
	
	public int recur(TreeNode root) {
		if(root==null) {
			return 0;
		}
		int left = recur(root.left);
		int right = recur(root.right);
		if(left==-1||right==-1||Math.abs(right-left)>1) {			//左右子树不是搜索二叉树，返回-1
			return -1;
		}
		return Math.max(left, right)+1;								//返回层级+1
	}
