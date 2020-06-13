	public int[] twoSum(int[] nums, int target) {
		int[]sum = new int[2];
		
		for (int i = 0; i < nums.length; i++) {
			for (int j = i+1; j < nums.length; j++) {
				if(nums[i]+nums[j]==target) {
					sum[0]=i;
					sum[1]=j;
					break;
				}
				
			}
		}
		
		return sum;
	}
	

    public int[] twoSum(int[] nums, int target) {
        int[]sum = new int[2];
		HashMap<Integer, Integer> map = new HashMap<Integer, Integer>(); 
		for (int i = 0; i < nums.length; i++) {
			
			if(map.containsKey(target-nums[i])) {
				sum[0]=map.get(target-nums[i]);
				sum[1]=i;
			}
            map.put(nums[i], i);
		}
		
		return sum;
}
