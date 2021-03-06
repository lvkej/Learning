    public int strToInt(String str) {
        char[] arr = str.trim().toCharArray();
        if(arr.length==0){
            return 0;
        }
        int isNeg = 1,boundry=Integer.MAX_VALUE/10,res=0;
        if(arr[0]=='+'){
            isNeg=1;
        }else if(arr[0]=='-'){
            isNeg=-1;
        }


        for(int i=0;i<arr.length;i++){
            char c = arr[i];
            if(i==0&&(c=='+'||c=='-')){
                continue;
            }
            if(c<'0'||c>'9'){
                break;
            }
            if(res>boundry||((res==boundry)&&c>'7')){
                return isNeg==1 ? Integer.MAX_VALUE : Integer.MIN_VALUE;
            }
            res=res*10+(c-'0');
        }

        return isNeg==1 ? res : -res;

    }
