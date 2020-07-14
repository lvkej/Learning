    //求一个数组中最大值-最小值小于N的子数组个数。任何符合该条件的数组的子数组都符合，不符合的数组再加后续字符也不符合
	public static int getnum(int[]arr, int n) {
		if(arr==null||arr.length==0) {
			return 0;
		}
		int res = 0;
		int l =0;					//l,r都是从0-arr.length,不回退，时间复杂度O(N)
		int r = 0;
		LinkedList<Integer> qmax = new LinkedList<Integer>();//大双向链表-按从大到小排列,第一个是最大的。
		LinkedList<Integer> qmin = new LinkedList<Integer>();//小链表-按从小到大排列
		while(l<arr.length) {
			while(r<arr.length) {
				if(!qmin.isEmpty()&&arr[qmin.peekLast()]>=arr[r]) { //等于也删，重新add
					qmin.pollLast();
				}
				qmin.addLast(r);
				
				if(!qmax.isEmpty()&&arr[qmax.peekLast()]<=arr[r]) {
					qmax.pollLast();
				}
				qmax.addLast(r);
				
				if(arr[qmax.peekFirst()]-arr[qmin.peekFirst()]>=n) {
					break;
				}else {
					r++;
				}
							
			
			}
			res+=r-l;
			if(qmax.peekFirst()==l) {			//看第一个是否是l，若是则要poll
				qmax.pollFirst();
			}
			if(qmin.peekFirst()==l) {
				qmin.pollFirst();
			}
			l++;
		}
		return res;
	}
