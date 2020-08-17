    public static int hammingWeight(int n) {
		 int res = 0;
		 while(n!=0) {        
			 res+=n&1;                  //按位与运算
			 n>>>=1;                    //无符号位右移1格
		 }
		 return res;		 
	 }
   
      public int hammingWeight(int n) {
     int res = 0;
      while(n!=0) {
     res+=1;
     n&=(n-1);                    //n与n-1&,去除最右端1
     }
    return res;
    }
