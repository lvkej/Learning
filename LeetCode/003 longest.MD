
public int lengthOfLongestSubstring(String s) {
        	int max=0,i=0,j=0;//另设j变量！
		HashSet<Character> c = new HashSet<Character>();
		while(i < s.length()) {
			if(!c.contains(s.charAt(i))) {                    //s.charat(index);
				c.add(s.charAt(i++));
				max=Math.max(max, c.size());                     //math.max
			}
			else {
				c.remove(s.charAt(j++));                //从头开始删除，一直删到重复的那个，不然进不了i循环
			}
			
		}
		return max;
    }
