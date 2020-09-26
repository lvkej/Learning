    //dp
	    public int maxProfit(int[] prices) {
		int cost = Integer.MAX_VALUE, profit = 0;
		for(int each:prices) {
			cost = Math.min(cost, each);
			profit = Math.max(profit, each-cost);		//dp[i] = math.max(dp[i-1],price-cost)
		}
		return profit;
	}
