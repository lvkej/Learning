    class Solution {
    int cnt;
    public int numWays(int n, int[][] relation, int k) {
        Map<Integer, Set<Integer>> map = new HashMap<>();
        for (int[] ints : relation) {
            if(!map.containsKey(ints[0])){
                Set<Integer> set = new HashSet<>();
                set.add(ints[1]);
                map.put(ints[0],set);
            }else {
                map.get(ints[0]).add(ints[1]);
            }
        }
        dfs(0,0,n,k,map);
        return cnt;
    }
    public void dfs(int curStep,int curIndex,int n,int k,Map<Integer,Set<Integer>> map){

        if(curStep==k){
            if(curIndex==n-1)
            cnt++;
            return;
        }
        Set<Integer> nextSet = map.get(curIndex);
        if(nextSet!=null){
            for (Integer nextIndex : nextSet) {
                dfs(curStep+1,nextIndex,n,k,map);
            }
        }
    }
    }
    
    //dp
    class Solution {
    public int numWays(int n, int[][] relation, int k) {
        int[][] dp = new int[k+1][n];
        dp[0][0]=1;
        for(int i =1;i<=k;i++){
            for(int[] ints : relation){
                int a =ints[0];
                int b = ints[1];
                dp[i][b] += dp[i-1][a];
            }
        }
        return dp[k][n-1];
    }
    }
