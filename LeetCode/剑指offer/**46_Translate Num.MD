    public int translateNum(int num) {		
		String s = String.valueOf(num);
		int a = 1;											//dp[1]
		int b = 1;											//dp[0]
		for(int i =2;i<=s.length();i++) {
			String tmp = s.substring(i-2, i);							//判断10*i-1 + i 是否存在
			int c = tmp.compareTo("10")>=0 &&tmp.compareTo("25")<=0 ? a+b :a;
			b=a;
			a=c;
		}
		return a;		
    }
	
	public int translateNum(int num) {
		int a=1,b=1,x,y=num%10;
		while(num!=0) {
			num/=10;
			x=num%10;								//十位数
			int tmp = 10*x+y;						//y是个位数
			int c = tmp>=10&&tmp<=25 ? a+b : a;		
			b=a;
			a=c;
			y=x;									//y=x
		}
		return a;
		
    }
