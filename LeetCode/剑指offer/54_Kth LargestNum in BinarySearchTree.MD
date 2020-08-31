    public int kthLargest(TreeNode root, int k) {
		Stack<TreeNode> s = new Stack<>();
		TreeNode cur = root.right;
		int res = 0;
		int cnt=0;
		s.push(root);
		while(!s.isEmpty()||cur!=null) {			
			if(cur!=null) {
				s.push(cur);
				cur=cur.right;
			}else {
				cur=s.pop();
				if(++cnt==k) {
					res = cur.val;
					break;
				}
				cur=cur.left;
			}
			
		}
		return res;
    }
	
  
      int k,res;
	public int kthLargest(TreeNode root, int k) {
		this.k=k;
		dfs(root);
		return res;
	}
	public void dfs(TreeNode root) {
		if(root==null) {
			return;
		}
		dfs(root.right);

		if(k==0)return;
		if(--k==0) res=root.val;
		
		dfs(root.left);
	}
