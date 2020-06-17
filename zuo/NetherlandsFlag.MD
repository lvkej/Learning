    public static int[] partition(int[] arr, int l, int r, int p) {

		return new int[] { less + 1, more - 1 };
		int less = l-1;               //less和more分别为小于部分的右边界和大于部分的左边界
		int more = r+1;
		int cur = l;
		while(cur<more) {
			if(arr[cur]<p) {
				swap(arr,++less,cur++);
			}else if(arr[cur]>p) {
				swap(arr,--more,cur);//由于交换后未知cur的具体值，cur不变
			}else {
				cur++;
			}
		}
		return new int[] {less+1,more-1};
	}
