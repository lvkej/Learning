    public int majorityElement(int[] nums) {
		int sum=0;
		int major=0,count=0;
		for (int i = 0; i < nums.length; i++) {
			if(sum==0) {
				major=i;
				
			}
			sum+= nums[major]==nums[i] ? 1 : -1 ;
		}
		
		for (int each:nums) {
			count= each==nums[major] ? count+1 :count;
		}
		return count>nums.length /2 ?nums[major] : 0;
    }
