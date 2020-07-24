    //给定一个长度大于1的字符串，我们可以把这个字符串分成两个非空的部分，我们说s1的搅乱串，指的是在任意一种分解结构中，随意交换某个节点的左
    右两个孩子所形成的字符串//

    public static boolean is(String s1, String s2) {
		if(s1.length()!=s2.length()) {
			return false;
		}
		if(s1.equals(s2)) {
			return true;
		}
		int N = s1.length();
		return func(s1.toCharArray(),s2.toCharArray(),0,0,N);
	}
	
	public static boolean func(char[] chs1,char[] chs2, int l1,int l2, int size) {
		if(size==1) {
			return chs1[l1]==chs2[l2];			//basecase
		}
		for (int i = 1; i < size; i++) {
			if((func(chs1,chs2,l1,l2,i)&&func(chs1,chs2,l1+i,l2+1,size-i))
					||
					(func(chs1,chs2,l1,l2+size-i,i)&&func(chs1,chs2,l1+i,l2,size-i))) {
				return true;
			}
		}
		return false;
	}
	
	public static boolean isdp(String s1,String s2) {
		if(s1.length()!=s2.length()) {
			return false;
		}
		if(s1.equals(s2)) {
			return true;
		}
		char[] chs1=s1.toCharArray();
		char[] chs2=s2.toCharArray();
		int N =s1.length();
		boolean[][][] dp = new boolean[N][N][N+1];			//l1,l2,size;size取1-N，故N+1
		
		for (int i = 0; i <N; i++) {
			for (int j = 0; j < N; j++) {
				dp[i][j][1] = chs1[i]==chs2[j];
			}
		}
	
		for (int size = 2; size < N+1; size++) {
			for (int l1 = 0; l1 < N-size; l1++) {					//L1取值细节，L1+size<N
				for (int l2 = 0; l2 < N-size; l2++) {
					for (int part = 1; part < size; part++) {
									
						if((dp[l1][l2][part]&&dp[l1+part][l2+part][size-part])
								||
								(dp[l1][l2+size-part][part]&&dp[l1+part][l2][size-part])) {
							dp[l1][l2][size]= true;
							break;									//break从part的循环中退出
						}
					}
				}
			}
		}
		return dp[0][0][N];
	}
