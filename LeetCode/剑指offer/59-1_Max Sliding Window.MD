    public int[] maxSlidingWindow(int[] nums, int k) {
		if(nums.length==0||k==0) {
			return new int[0];
		}
		LinkedList<Integer> que = new LinkedList<Integer>();
		int[] res = new int[nums.length-k+1];
		for(int i =0;i<k;i++) {
			while(!que.isEmpty()&&nums[i]>que.peekLast()) {
				que.removeLast();
			}
			que.addLast(nums[i]);
		}
		
		for(int i =k;i<nums.length;i++) {
			res[i-k]=que.peekFirst();
			if(que.peekFirst()==nums[i-k]) {
				que.removeFirst();
			}
			while(!que.isEmpty()&&nums[i]>que.peekLast()) {
				que.pollLast();
			}
			que.addLast(nums[i]);
		}
		res[nums.length-k]=que.peekFirst();
		return res;
    }
