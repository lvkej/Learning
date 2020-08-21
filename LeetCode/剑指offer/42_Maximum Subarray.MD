    public static int maxSubArray(int[] nums) {
        int sum = 0,res=0;
        int index = 0;
        while(index<nums.length){
            if(sum<0){
                sum=0;
            }
            sum+=nums[index];
            res=Math.max(Math.max(res, sum),nums[index]);
            index++;
        }
        return res;
    }
