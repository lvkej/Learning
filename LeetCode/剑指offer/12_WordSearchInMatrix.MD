    public boolean exist(char[][] board, String word) {
		if(board==null||board.length<1||word==null) {
			return false;
		}
		char[] chs = word.toCharArray();
		boolean res = false;
		for (int i = 0; i < board.length; i++) {
			for (int j = 0; j < board[0].length; j++) {
				if(dfs(i,j,board,chs,0)==true) {
					return true;
				}
			}
		}
		return res;
    }
	
	public boolean dfs(int i,int j,char[][]board,char[]chs,int cur) {
		if(i<0||i>=board.length||j<0||j>board[0].length||board[i][j]!=chs[cur]) {
			return false;
		}
		if(cur==chs.length-1) {
			return true;
		}
		char tmp = board[i][j];											//标记这一位置已经来过了
		board[i][j] = '/';
		boolean res = dfs(i+1,j,board,chs,cur+1)||dfs(i-1,j,board,chs,cur+1)
					||dfs(i,j+1,board,chs,cur+1)||dfs(i,j-1,board,chs,cur+1);
		board[i][j] = tmp;												//还原标记
		return res;	
	}
