
	  public static int getmaxE(int[] arr) { 					//O(log(N2))
		int res = Integer.MIN_VALUE;
		int[] dp= new int[arr.length];		//设置dp记录0-i的异或和
		int eor = 0;						//全局变量，记录总异或和
		for (int i = 0; i < arr.length; i++) {
			eor^=arr[i];
			res = Math.max(res, eor);
			for (int start = 0; start < i; start++) {
				int cur = eor^dp[start];				//e1^e2=e3 ---e1=e2^e3;e2=e1^e3;e(s+1-i)=e(0-s)^e(0-i)
				res = Math.max(res, cur);
			}
			dp[i] = eor;					//dp[i]记录0-i异或和eor			
		}
		return res;
	}
	
	public static class Node {								//O(log(N))
		public Node[] nexts = new Node[2];
	}

	public static class NumTrie {
		public Node head = new Node();				//设置头节点

		public void add(int num) {
			Node cur = head;
			for (int move = 31; move>=0; move--) {				//int32位，移动32次，从高位开始
				int path = ((num>>move)&1);						//与1&，
				cur.nexts[path] = cur.nexts[path]==null ? new Node() : cur.nexts[path];
				cur=cur.nexts[path];
			}
		}

		public int maxXor(int num) {					//求以i结尾的最大异或和，找每一位是否有异或为1的
			Node cur = head;
			int res = 0;
			for (int move = 31; move >= 0; move--) {
				int path = (num>>move) & 1;
				int best = move==31? path : (path^1);			//最佳路径分类，符号位就是path，其他是path^1
				best = cur.nexts[best]!=null ? best : (best^1); 		//best是否存在；
				res |= (path^best)<<move;						//res或运算 path^best，左移move位
				cur = cur.nexts[best];	
			}
			return res;
		}

	}

	public static int maxXorSubarray(int[] arr) {
		
		if (arr == null || arr.length == 0) {
			return 0;
		}
		int max = Integer.MIN_VALUE;
		int eor = 0;
		NumTrie numTrie = new NumTrie();
		numTrie.add(0);										//初始值0
		for (int i = 0; i < arr.length; i++) {
			eor ^= arr[i];									//全局变量记录0-i的异或和
			max = Math.max(max, numTrie.maxXor(eor));		//e(x-i)=e(0-i)^e(0-x),利用maxxor函数查看是否有最大值
			numTrie.add(eor);								//eor 加入n中
		}
		return max;
	}
