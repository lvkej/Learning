    public double myPow(double x, int n) {
		 if(x==0) {
			 return 0;
		 }
		 
		 long b = n;					//若n是-2-31次方，b=-b就越界了，选用long
		 double res = 1.0;
		 
		 if(n<0) {
			 x=1/x;
			 b=-b;
		 }
		 
		 while(b!=0) {
			 res*= (b&1)==1 ? x : 1;		//b与1与，看最后一位是否是1
			 x*=x;										//快速幂法 时间复杂度O(logn)
			 b >>=1;							
		 }
		 return res;

	 }
   
    public class Solution {
    public double pow(double x, int n) {
        if(n == 0)
            return 1;
        if(n<0){
            n = -n;
            x = 1/x;
        }
        return (n%2 == 0) ? pow(x*x, n/2) : x*pow(x*x, n/2);      //递归
    }
    } 
