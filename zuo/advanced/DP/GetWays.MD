    //start开始end结束，共可以走step步，求有几种走法//
    public static int getways(int total,int start,int step,int end) {
		if(start<1||start>total||end<1||end>total||step<0) {		//边界条件
			return 0;
		}
		int res=0;
		if(step==0) {
			res= start==end ? 1 : 0;
		}else {
			if(start==1) {
				res=getways(total,start+1,step-1,end);
			}else if(start==total) {
				res=getways(total,start-1,step-1,end);
			}else {
				res=getways(total,start+1,step-1,end)+getways(total,start-1,step-1,end);				
			}
		}
		return res;
	}
	
	public static int dp(int total,int start,int step,int end) {
		int[][]dp = new int[step+1][total];
		dp[0][end-1]=1;
		for (int i = 1; i < dp.length; i++) {
			for (int j = 0; j < dp[0].length; j++) {
				if(j==0) {
					dp[i][j]=dp[i-1][j+1];
				}else if(j==total-1) {
					dp[i][j]=dp[i-1][j-1];
				}else {
					dp[i][j]=dp[i-1][j-1]+dp[i-1][j+1];
				}
			}
		}
		return dp[step][start-1];
	
	}
