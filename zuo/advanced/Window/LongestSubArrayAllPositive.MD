    //数组中全是正数，求累加和位aim的最长子数组//
    public static int get(int[]arr,int aim) {
		if(arr.length<1||arr==null||aim<0) {
			return 0;
		}
		return maxlength(arr,0,0,0,aim);
	}
	
	public static int maxlength(int[] arr,int curnum, int len,int sum,int aim) {
		int res = 0;
		if(curnum==arr.length) {
			if(sum==aim) {
				return len;
			}else {
				return 0;
			}
		}else {						//子数组是连续的，所以这个不对！！！！
			res=Math.max(maxlength(arr,curnum+1,len+1,sum+arr[curnum],aim), maxlength(arr,curnum+1,len,sum,aim));
		}
		return res;
	}
	
	public static int getMaxLength(int[] arr, int k) {				//双指针窗口
		if (arr == null || arr.length == 0 || k <= 0) {
			return 0;
		}
		int L = 0;
		int R = 0;
		int sum = arr[0];
		int len = 0;
		while (R < arr.length) {
			if (sum == k) {
				len = Math.max(len, R - L + 1);
				sum -= arr[L++];
			} else if (sum < k) {
				R++;
				if (R == arr.length) {
					break;
				}
				sum += arr[R];
			} else {
				sum -= arr[L++];
			}
		}
		return len;
	}
