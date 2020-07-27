    //数组中有一个数出现了奇数次，数组中有两个数出现了奇数次，数组中有一个数出现1次，剩下的数出现了k次//
    public static int OneOdd(int[]arr) {
		int eor=0;
		for(int each:arr) {
			eor^=each;					//偶数个相同的数异或和为0，异或到最后剩奇数的数
		}
		return eor;
	}
	
	public static void TwoOdd(int[]arr) {
		int eor = 0;
		for(int each:arr) {
			eor^=each;						//eor结果就是a^b(两个奇数)
		}
		
		int e = eor&(~eor+1);				//eor取反加一和eor与，得到eor中为1的一位，ab中有且只有一个这一位是1
		
		int e1 = 0;
		for (int i = 0; i < arr.length; i++) {
			if((e&arr[i])!=0) {				//若和e与不为0，则同一位也为1
				e1^=arr[i];					
			}
		}									//找到a或b，eor^e1=a^b^a=b,
		
		System.out.println(e1+" "+(e1^eor));
	}
	
	public static int ktimes(int[]arr,int k) {
		int[] e = new int[32];							//2进制32位就够了，保险起见用32个单元的数组
		for (int i = 0; i < arr.length; i++) {
			getsum(e,arr[i],k);
		}
		int res = getnumfromksys(e,k);
		return res;
	}
	
	public static void getsum(int[]e,int i,int k) {
		int e0[] = getksys(i,k);
		for (int j = 0; j < e0.length; j++) {
			e[j]=(e[j]+e0[j])%k;						//加入就%防越界
		}
		
	}
	
	public static int[] getksys(int i,int k) {			//将数arr[i]转化为k进制存入数组中
		int e[] = new int[32];
		int index = 0;
		while(i!=0) {
			e[index++]=i%k;
			i/=k;
		}
		return e;
	}
	
	public static int getnumfromksys(int[]e,int k) {			//k进制转十进制
		int res = 0;
		for (int i = e.length-1; i >=0; i--) {
			res*=k;
			res+= e[i];			
		}
		return res;
	}
