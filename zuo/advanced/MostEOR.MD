    public class Most_EOR {

	//^异或，0^n=n;n^n=0;
	public static int mostEOR(int[] arr) {
		int ans = 0;
		int xor = 0;
		int[] mosts = new int[arr.length];
		HashMap<Integer, Integer> map = new HashMap<>();
		map.put(0, -1);
		for (int i = 0; i < arr.length; i++) {
			xor ^= arr[i];
			if (map.containsKey(xor)) {//若以i结尾是最优解，则前k个异或和也为sum，因为sum^0=sum;
				int pre = map.get(xor);
				mosts[i] = pre == -1 ? 1 : (mosts[pre] + 1);//若存在，dp[i]=dp[k]+1
			}
			if (i > 0) {
				mosts[i] = Math.max(mosts[i - 1], mosts[i]);//若不存在，dp[i]=dp[i-1],和前一个作比较
			}
			map.put(xor, i);
			ans = Math.max(ans, mosts[i]);
		}
		return ans;
	}
