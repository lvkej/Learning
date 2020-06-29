    public static void main(String[] args) {
		int[] arr = new int[1000]; //32000bit
		int index=30000;			//把30000个bit位上描黑
		int intindex=index/32;			//每个int有4个bite，一个bite8bit，1int=32bit，找到对应的int
		int bitindex=index%32;			//确定bit位置
		
		arr[intindex] = (arr[intindex]|(1<<bitindex));
	}
