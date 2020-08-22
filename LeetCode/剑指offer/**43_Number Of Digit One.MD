    public int countDigitOne(int n) {
		int dig =1,res=0;
		int high = n/10,cur=n%10,low=0;
		while(high!=0||cur!=0) {
			if(cur==0) {
				res+=high*dig;                    //
			}else if(cur==1) {
				res+=high*dig+low+1;              //
			}else {
				res+=(high+1)*dig;                //
			}
			low+=cur*dig;
			dig*=10;
			cur=high%10;
			high/=10;
		}
		return res;
    }
