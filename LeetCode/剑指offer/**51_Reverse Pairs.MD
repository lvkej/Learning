    static int res = 0;
	public static int reversePairs(int[] nums) {
		if(nums==null||nums.length<2) {
			return 0;
		}
		
		mergesort(nums,0,nums.length-1);
		return res;
    }
	
	public static void mergesort(int[]nums,int l,int r) {
		if(l==r) {
			return;
		}
		int mid = (l+r)/2;
		mergesort(nums,l,mid);
		mergesort(nums,mid+1,r);
		merge(nums,l,mid,r);
	}
	
	public static void merge(int[]nums,int l ,int mid, int r) {
		int[] help = new int[r-l+1];
		int index = 0,p1=l,p2=mid+1;
		while(p1<=mid&&p2<=r) {
			if(nums[p1]>nums[p2]) {
				help[index++]=nums[p2++];
			}else {
				res+=p2-mid-1;									//nums[p1]<nums[p2],产生逆序对，对数是p2-mid-1
				help[index++]=nums[p1++];
			}
		}
		while(p1<=mid) {
			help[index++]=nums[p1++];							//p1没走完，剩下的逆序对数r-mid
			res+=r-mid;
		}
		while(p2<=r) {
			help[index++]=nums[p2++];
		}
		for (int i = 0; i < help.length; i++) {
			nums[l+i]=help[i];
		}
	}
