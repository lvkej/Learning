    public static int pro(int[][] matrix, int i,int j) {
		if(i==matrix.length-1&&j==matrix[0].length-1) {
			return matrix[i][j];
		}else if(i==matrix.length-1) {
			return matrix[i][j]+pro(matrix,i,j+1);
		}else if(j==matrix[0].length-1) {
			return matrix[i][j]+pro(matrix,i+1,j);
		}
		int right = pro(matrix, i, j+1)+matrix[i][j];
		int down = pro(matrix, i+1, j)+matrix[i][j];
		return Math.min(right, down);
	}
	
	public static int pro2(int[][] matrix) {
		int[][] dp = new int[matrix.length][matrix[0].length];
		dp[matrix.length-1][matrix[0].length-1]=matrix[matrix.length-1][matrix[0].length-1];
		
		for (int i = matrix.length-2; i >=0 ; i--) {
			dp[i][matrix[0].length-1] = dp[i+1][matrix[0].length-1]+ matrix[i][matrix[0].length-1];
		}
		
		for (int i = matrix[0].length-2; i >=0 ; i--) {
			dp[matrix.length-1][i] = dp[matrix.length-1][i+1]+ matrix[matrix.length-1][i];
		}
		
		for(int i=matrix.length-2;i>=0;i--) {
			for(int j=matrix[0].length-2;j>=0;j--) {
				dp[i][j] = Math.min(dp[i+1][j],dp[i][j+1])+matrix[i][j];
			}
		}
		return dp[0][0];
	}
