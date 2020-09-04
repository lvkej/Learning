    public String reverseWords(String s) {
		s=s.trim();											//去除头尾空格	
		int i=s.length()-1,j=i;								//双指针ij
		StringBuilder sb = new StringBuilder();
		while(i>=0) {
			while(i>=0&&s.charAt(i)!=' ') {							//找到第一个单词的头	
				i--;
			}
			sb.append(s.substring(i+1, j+1)+" ");							//substring i+1包含 j+1不包
			while(i>=0&&s.charAt(i)==' ') {							//找到下一个单词的尾
				i--;
			}
			j=i;
		}
		return sb.toString().trim();
    }
