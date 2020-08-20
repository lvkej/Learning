    //快排
    
    public int[] quicksort(int[]arr,int left,int right,int k) {
		
		int origin = right;
		int index=left;
		while(index<origin) {
			if(arr[index]<arr[origin]) {
				index++;
			}else {
				swap(arr,index,--origin);
			}
			
		}
		swap(arr,right,origin);
		
		if(origin==k-1) {                                             //如果右指针到了k-1就退出
			return Arrays.copyOf(arr, k);
		}
		
		return origin>k-1 ? quicksort(arr,left,origin-1,k) : quicksort(arr,origin+1,right,k);
	}
  
     //大根堆
     public int[] getLeastNumbers(int[] arr, int k) {
		if(k==0||arr.length==0) {
			return new int[0];
		}
		Queue<Integer> pq = new PriorityQueue<Integer>((x1,x2)->x2-x1);				//优先级队列，默认是小根堆，修改比较器为大根堆
		for(int each:arr) {
			if(pq.size()<k) {
				pq.offer(each);
			}else if(each<pq.peek()) {
				pq.poll();
				pq.offer(each);
			}
		}
		
		int[] res = new int[k];
		for(int i = 0;i<k;i++) {
			res[i]=pq.poll();
		}
		return res;
		
    }
