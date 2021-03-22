class Solution {
    private boolean[][] visited;
    public boolean exist(char[][] board, String word) {
        visited = new boolean[board.length][board[0].length];
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board[0].length;j++){
                if(board[i][j]==word.charAt(0)&&dfs(i,j,board,word,0)){
                    return true;
                }
            }
        }
        return false;

    }

    public boolean dfs(int i,int j,char[][]board,String word,int index){
        if(index==word.length()){
            return true;
        }
        if(i>board.length-1||i<0||j>board[0].length-1||j<0||visited[i][j]==true||board[i][j]!=word.charAt(index)){
            return false;
        }
        visited[i][j]=true;
        if(dfs(i+1,j,board,word,index+1)||dfs(i-1,j,board,word,index+1)||dfs(i,j+1,board,word,index+1)||dfs(i,j-1,board,word,index+1)){
            return true;
        }
        visited[i][j]=false;
        return false;

    }
}
