    public static boolean money2(int[] arr, int aim) {
		boolean[][] dp = new boolean[arr.length + 1][aim + 1];
		for (int i = 0; i < dp.length; i++) {
			dp[i][aim] = true;
		}
		for (int i = arr.length - 1; i >= 0; i--) {
			for (int j = aim - 1; j >= 0; j--) {
				dp[i][j] = dp[i + 1][j];
				if (j + arr[i] <= aim) {
					dp[i][j] = dp[i][j] || dp[i + 1][j + arr[i]];
				}
			}
		}
		return dp[0][0];
	}
	
	public static boolean money3(int[] arr,int sum,int index,int aim) {
		if(index==arr.length) {
			return sum==aim;				//basecase 若==返回true，若！=返回false
		}
		return money3(arr, sum+arr[index], index+1, aim)||money3(arr, sum, index+1, aim);
		//只要basecase是true，就都返回true
	} 
	
