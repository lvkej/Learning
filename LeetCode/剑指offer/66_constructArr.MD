    public int[] constructArr(int[] a) {
        int[] b = new int[a.length];
        for(int i=0,pro=1;i<a.length;i++){
            b[i]=pro;
            pro*=a[i];
        }
        for(int i=a.length-1,pro=1;i>=0;i--){
            b[i]*=pro;
            pro*=a[i];
        }
        return b;
    }
