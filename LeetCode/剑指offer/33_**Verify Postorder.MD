    //递归版
    
    public boolean verifyPostorder(int[] postorder) {
		 
		 return recur(postorder,0,postorder.length-1);
	 }
	 
	 public boolean recur(int[]postorder,int i,int j) {
		 if(i>=j) {
			 return true;
		 }
		 
		 int p = i;
		 while(postorder[p]<postorder[j]) {									//二叉搜索树root的所有左树都小于root
			 p++;
		 }
		 int pl =p-1;
		 
		 while(postorder[p]>postorder[j]) {
			 p++;
		 }
		 
		 return p==j&&recur(postorder,i,pl)&&recur(postorder,pl+1,j-1);	//首先判断p是否走到尾
	 }
   
    //单调栈
    
    public boolean verifyPostorder(int[] postorder) {
		 Stack<Integer> s = new Stack<Integer>();
		 int root = Integer.MAX_VALUE;								//初始假设root无限大，所有节点都是root的左子树
		 
		 for (int i = postorder.length-1; i >=0; i--) {
			if(postorder[i]>root) {									//改变root条件是出现左节点，当改变root后，所有子树值都要小于root
				return false;
			}
			
			while(!s.isEmpty()&&s.peek()>postorder[i]) {			//当栈中数大于数组数，意味出现左节点，更换root
																	//root替换直到栈顶数小于数组当前数
				root=s.pop();
			}
			
			s.push(postorder[i]);
		}
		 
		 return true;
		
	 }
