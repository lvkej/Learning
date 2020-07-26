    //一个字符串，求最小的切数，将其全部分割为回文串//
    public static int solution(String str) {
		if(str==null||str.length()==0) {
			return 0;
		}
		return getcut(str.toCharArray(),0);
	}

	public static int getcut(char[] arr,int i) {
		
		if(i==arr.length) {
			return -1;
		}
		
		int min = Integer.MAX_VALUE;
		for (int j = i; j < arr.length; j++) {
			if(isp(arr,i,j)) {
				min=Math.min(min, getcut(arr,j+1));
			}
		}		
		return min+1;
	}
	
	public static boolean isp(char[]arr,int start, int end) {
		while(start<end) {
			if(arr[start++]!=arr[end--]) {
				return false;
			}			
		}
		return true;
	}
	
	public static int minCut(String str) {
		if (str == null || str.equals("")) {
			return 0;
		}
		char[] chas = str.toCharArray();
		int len = chas.length;
		int[] dp = new int[len + 1];
		dp[len] = -1;
		boolean[][] p = new boolean[len][len];			//对数组进行预处理，
		for (int i = len - 1; i >= 0; i--) {
			dp[i] = Integer.MAX_VALUE;
			for (int j = i; j < len; j++) {
				if (chas[i] == chas[j] && (j - i < 2 || p[i + 1][j - 1])) {		//j-i==1,或者i+1,j-1相等，从len-1开始推
					p[i][j] = true;
					dp[i] = Math.min(dp[i], dp[j + 1] + 1);
				}
			}
		}
		return dp[0];
	}
