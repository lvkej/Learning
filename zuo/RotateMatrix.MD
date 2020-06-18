    public static void rotate(int[][]matrix) {
		int tr =0;
		int tc =0;
		int dr =matrix.length-1;
		int dc = matrix[0].length-1;  //右下角列数为matrix[0].lenth-1
		while(tr<dr) {
			rotateEdge(matrix,tr++,tc++,dr--,dc--);                //一圈圈向内旋转。
		}
	}
	public static void rotateEdge(int[][]matrix,int tr, int tc, int dr, int dc) {
		int cnt = dr-tr;                              //需要旋转几个数
		for (int i = 0; i < cnt; i++) {
			int tem = matrix[tr][tc+i];
			matrix[tr][tc+i]=matrix[dr-i][tc];
			matrix[dr-i][tc]=matrix[dr][dc-i];          //扣边界
			matrix[dr][dc-i]=matrix[tr+i][dc];
			matrix[tr+i][dc]=tem;
		}
	}
