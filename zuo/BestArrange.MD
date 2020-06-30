    public static class Program {
		public int start;
		public int end;

		public Program(int start, int end) {
			this.start = start;
			this.end = end;
		}
	}
	
	public static class ProgramComparator implements Comparator<Program>{

		@Override
		public int compare(Program o1, Program o2) {
			return o1.end-o2.end;									//贪心算法，做先结束的项目
		}
		
	}



	public static int bestarrange(Program[] programs,int cur) {
		Arrays.sort(programs,new ProgramComparator());					//按结束时间排序
		int res=0;
		for (int i = 0; i < programs.length; i++) {
			if(cur<=programs[i].start) {
				res++;
				cur=programs[i].end;
			}
		}
		return res;
		
	}
