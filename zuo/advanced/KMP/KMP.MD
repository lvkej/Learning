    public static int getIndexOf(String s1,String s2) {
		if(s1==null||s2==null||s1.length()<1||s2.length()<1) {
			return -1;
		}
		char[] str1 = s1.toCharArray();
		char[] str2 = s2.toCharArray();
		int i1 = 0;
		int i2 = 0;
		int [] next = getnext(str2);
		while(i1<str1.length&&i2<str2.length) {
			if(str1[i1]==str2[i2]) {			//如果字符相同，i1i2各前进一格
				i1++;
				i2++;
			}else if(next[i2]>-1) {				//next[1]==0，next[0]==-1;若i2还没到0，就继续
				i2 = next[i2];
			}else {								//i2=0，i1++
				i1++;
			}
		}
		return i2==str2.length?i1-i2:-1;			//若i2==str2.length，说明存在。
	}
	
	public static int[] getnext(char[] s) {
		if (s.length == 1) {						//边界，length=1
			return new int[] { -1 };
		}
		int[] next = new int[s.length];
		next[0]=-1;
		next[1]=0;
		int cur = 0;		//最长前缀的长度cur；最长序列的下一个字符编号就是cur！
		int i = 2;			//当前的i
		while(i<s.length) {
			if(s[cur]==s[i-1]) {		//i-1的字符和最长序列的下一个字符即cur进行对比
				next[i++]=++cur;
			}else if(cur>0) {
				cur = next[cur];		//当cur还>0时，继续在cur前找最长前缀
			}else {
				next[i++]=0;			//cue=0时，若！=s[i-1],next[i++]=0
			}
		}
		return next;
	}
	
