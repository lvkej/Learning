    public int[] spiralOrder(int[][] matrix) {
        if(matrix==null||matrix.length<1||matrix[0].length<1){
        	int[] res = new int[0];
            return res;
        }
        ArrayList<Integer> helper = new ArrayList<Integer>();
        int row1 = 0,col1=0, row2 = matrix.length-1, col2 = matrix[0].length-1;
        help(row1,col1,row2,col2,matrix,helper);
        int[] a = new int[matrix.length*matrix[0].length];
        int index = 0;
        for(index=0;index<a.length;index++) {
        	a[index]=helper.get(index);
        }
        return a;
    }
	
	public void help(int row1,int col1,int row2,int col2,int[][]matrix,ArrayList<Integer> helper) {
		if(row1>row2||col1>col2) {
			return ;
		}
		if(row1==row2) {
			for (int i = col1; i <=col2; i++) {
				helper.add(matrix[row1][i]);
			}
		}
		if(col1==col2) {
			for (int i = row1; i <=row2; i++) {
				helper.add(matrix[i][col2]);
			}
		}
		
		for (int i = col1; i <col2; i++) {
			helper.add(matrix[row1][i]);
		}
		for (int i = row1; i <row2; i++) {
			helper.add(matrix[i][col2]);
		}
		for (int i = col2; i >col1; i--) {
			helper.add(matrix[row2][i]);
		}
		for (int i = row2; i >row1; i--) {
			helper.add(matrix[i][col1]);
		}
		
		help(row1+1,col1+1,row2-1,col2-1,matrix,helper);
	}
