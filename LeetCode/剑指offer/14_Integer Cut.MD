    public int cuttingRope(int n) {  
		if(n<=3) {
			return n-1;
		}
		int a = n/3,b=n%3;
		if(b==1) {
			return (int)Math.pow(3, a-1)*4;
		}else if(b==0) {
			return (int)Math.pow(3, a);
		}else {
			return (int)Math.pow(3, a)*2;
		}
    }
    
    public int cuttingRope(int n) {
        if(n <= 3) return n - 1;
        long res=1L;
        int p=(int)1e9+7;
        //贪心算法，优先切三，其次切二
        while(n>4){
            res=res*3%p;
            n-=3;
        }
        //出来循环只有三种情况，分别是n=2、3、4
        return (int)(res*n%p);
    }
