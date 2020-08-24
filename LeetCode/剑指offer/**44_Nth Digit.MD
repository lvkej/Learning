    public int findNthDigit(int n) {
		int digit = 1;				//位数
		long start = 1;				//开始的数字	
		long count = 9;				//这一位数总共有多少数位
		while(n>count) {
			n-=count;
			start*=10;
			digit++;
			count=digit*start*9;
		}											//1、找到属于那一位数
		long num = start+(n-1)/digit;				//2、找到属于哪一个数
		String s = String.valueOf(num);				//3、找到属于这一个数的哪一位
		return s.charAt((n-1)%digit)-'0';
    }
