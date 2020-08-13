    public static boolean findNumberIn2DArray(int[][] matrix, int target) {
		if(matrix.length==0||matrix==null) {
			return false;
		}
		
		int col = matrix.length;
		int rol = matrix[0].length  ;
		int curc = 0;
		int curr = rol-1;
		
		boolean res = false;
		while(curc<col&&curr>=0) {
			if(matrix[curc][curr]>target) {
				curr--;
			}else if(matrix[curc][curr]<target) {
				curc++;
			}else {
				res = true;
				break;
			}
		}
		
		return res;
		
    }
