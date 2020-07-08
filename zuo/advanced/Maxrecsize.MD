    public static int maxrecsize(int[][] map) {
		if(map==null||map.length==0||map[0].length==0) {
			return 0;
		}
		int max = 0;
		int[] height = new int[map[0].length];
		for (int i = 0; i < map.length; i++) {
			for (int j = 0; j < map[0].length; j++) {
				height[j]=map[i][j]==0?0:height[j]+1;//若有一个为零，则这列为零
			}
			max = Math.max(max, maxrecfrombottom(height));
		}
		return max;
	}
	
	public static int maxrecfrombottom(int[]height) {
		if(height==null||height.length<1) {
			return 0;
		}
		int max = 0;
		Stack<Integer> s = new Stack<Integer>();//建立最小单调栈
		
		for (int i = 0; i < height.length; i++) {
			while(!s.isEmpty()&&height[i]<=height[s.peek()]) {			//***单调栈的while格式***
				int j = s.pop();
				int k = s.isEmpty()?-1:s.peek();
				int curarea = height[j]*(i-k-1);
				max=Math.max(max, curarea);
			}
			s.push(i);
		}
		
		while(!s.isEmpty()) {		//遍历完后开始清栈
			int j = s.pop();
			int k = s.isEmpty()?-1:s.peek();
			int curarea = height[j]*(height.length-k-1);
			max=Math.max(max, curarea);
		}
		return max;
	}
