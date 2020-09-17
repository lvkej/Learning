    public int lastRemaining(int n, int m) {
		ArrayList<Integer> arr = new ArrayList<Integer>();
		for (int i = 0; i < n; i++) {
			arr.add(i);
		}
		
		int index = 0;
		int num = n;
		while(arr.size()>1) {
			index = (index+m-1)%num;
			arr.remove(index);
			num--;
		}
		return arr.get(0);
    }
