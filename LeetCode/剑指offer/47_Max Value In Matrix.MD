    public int maxValue(int[][] grid) {
		
		int[][] dp = new int[grid.length][grid[0].length];
		dp[grid.length][grid[0].length] = grid[grid.length][grid[0].length];
		for (int i = dp.length-2; i>=0 ; i--) {
			dp[i][grid[0].length-1]=dp[i+1][grid[0].length-1]+grid[i][grid[0].length-1];
		}
		for (int i = dp[0].length-2; i>=0 ; i--) {
			dp[grid.length-1][i]=dp[grid.length-1][i+1]+grid[grid.length-1][i];
		}
		for (int i = dp.length-2; i>=0 ; i--) {
			for (int j = dp[0].length-2; j>=0 ; j--) {
				dp[i][j]= Math.max(dp[i+1][j], dp[i][j+1])+grid[i][j];
			}
		}
		return dp[0][0];
    }
