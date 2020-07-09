    public static int maxLength1(int[] arr, int k) {//从头开始加，map中加入前i个数和，和sum-aim比较
		if(arr==null||arr.length ==0) {
			return 0;
		}
		HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
		map.put(0, -1);//第一个值
		int len = 0;
		int sum = 0;
		for (int i = 0; i < arr.length; i++) {
			sum+=arr[i];
			if(map.containsKey(sum-k)) {
				len = Math.max(len, i-map.get(sum-k));
			}
			if(!map.containsKey(sum-k)) {
				map.put(sum,i);
			}
		}
		return len;
	}
