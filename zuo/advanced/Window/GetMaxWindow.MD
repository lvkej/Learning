    public static int[] getmaxwin(int[] arr,int w) {
		if(arr==null||w<1||arr.length<w) {
			return null;
		}
		LinkedList<Integer> qmax = new LinkedList<Integer>();	//双向链表，记录的是坐标！
		int[]res = new int[arr.length-w+1];
		int index = 0;											//记录res中的坐标
		for (int i = 0; i < arr.length; i++) {
			
			while(!qmax.isEmpty()&&arr[qmax.peekLast()]<=arr[i]) {	//qmax不空，且加入值更大
				qmax.pollLast();		
			}
			qmax.addLast(i);							//qmax中add的是坐标
			
			if(qmax.peekFirst()==i-w) {					//若到了左边界，删除第一个
				qmax.pollFirst();
			}
			
			if(i>=w-1) {								//加入res【index】
				res[index++]=arr[qmax.peekFirst()];
			}
			
		}
		return res;
	}
