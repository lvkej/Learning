    class Solution {
    public TreeNode mirrorTree(TreeNode root) {
        if(root == null) return null;
        TreeNode tmp = root.left;
        root.left = mirrorTree(root.right);
        root.right = mirrorTree(tmp);
        return root;
    }
}

    //我写的
    public TreeNode mirrorTree(TreeNode root) {
		if(root==null){
			return root;
		}
		
		swap(root);
		
		return root;
    }
	
	public void swap(TreeNode node) {
		if(node==null) {
			return;
		}
		TreeNode tmp = node.left;
		node.left=node.right;
		node.right = tmp;
		
		swap(node.left);
		swap(node.right);
	}
}
