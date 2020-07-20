    public static int maxLengthAwesome1(int[]arr,int aim) {
		if(arr==null||arr.length<1) {
			return 0;
		}
		
		int[] sum = new int[arr.length];
		int[] end = new int[arr.length];
		sum[arr.length-1] = arr[arr.length-1];			//sum记录以i开头的子数组中，累加和最小的和
		end[arr.length-1] = arr.length-1;				//end记录最小累加和子数组的末端坐标
		
		for (int i = arr.length-2; i >=0; i--) {
			if(sum[i+1]<0) {							//如果sum[i+1]<0，就加arr[i]
				sum[i]=sum[i+1]+arr[i];
				end[i]=end[i+1];
			}else {
				sum[i]=arr[i];
				end[i]=i;
			}
		}
		
		int start = 0;
		int sums=0;
		int len = 0;
		int r = 0;
		for (start=0; start < end.length; start++) {
			while(r<arr.length && sums+sum[r]<=aim) {
				sums+=sum[r];
				r=end[r]+1;
			}
			sums-= r>start ? arr[start] : 0;			//如果r==start，说明没进while循环，sum[r]>aim
			len=Math.max(len, r-start);
			r=Math.max(r, start+1);							//若r没有进while循环，则r取i+1
		}
		return len;
			
	}
	//精髓——右边界不回退，保证时间复杂度O(N),
	//思维轨迹：舍弃无效答案，右边界不退，不关心更短的解。
