    public void spiralOrderPrint(int[][] matrix) {
  	int tr =0;
		int tc =0;
		int dr =matrix.length-1;
		int dc = matrix[0].length-1;  //右下角列数为matrix[0].lenth-1
		while(tr<=dr&&tc<=dc) {
			print(matrix,tr++,tc++,dr--,dc--);
		}
	}
	
	public void print(int[][]matrix, int tr, int tc, int dr, int dc) {
		if(tr==dr) {                                   //第一种特殊情况，在同一行
			while(tc<=dc) {
				System.out.print(matrix[tr][tc++]+" ");
			}
		}else if(tc==dc) {                              //第二种特殊情况，在同一列
			while(tr<=dr) {
				System.out.print(matrix[tc][tr++]+" ");
			}
		}else {
			int curr=tr;
			int curc=tc;
			while(curc<dc) {
				System.out.print(matrix[curr][curc++]+" ");
			}
			while(curr<dr) {
				System.out.print(matrix[curr++][curc]+" ");
			}
			while(curc>tc) {
				System.out.print(matrix[curr][curc--]+" ");
			}
			while(curr>tc) {
				System.out.print(matrix[curr--][curc]+" ");
			}
		}
		
	}
