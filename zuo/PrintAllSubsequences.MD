    public static void printsub(char[] chs,int i ,String s) {
		if(i==chs.length) {
			System.out.println(s);
			return;
		}
		printsub(chs,i+1,s+String.valueOf(chs[i]));		//string.valueof()将字符改为string，integer.valueof一样
		printsub(chs,i+1,s);							//到每个字符都有两种情况，可加可不加。
	}
	
