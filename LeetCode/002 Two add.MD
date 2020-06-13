

	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
		ListNode l3 = new ListNode(0);
		ListNode tem3 = l3,tem1=l1,tem2=l2;
		int reg=0,sum=0;
		while(tem1!=null||tem2!=null) {
			int x = (tem1!=null)?tem1.val:0;                 //?:三目运算符
			int y = (tem2!=null)?tem2.val:0;
			sum=reg+x+y;                           //reg加入。
			
			tem3.next=new ListNode(sum%10);            //在listnode中已经有了构造函数，因此跳过一个。
			reg=sum/10;
			tem3=tem3.next;
			if(tem1!=null)tem1=tem1.next;
			if(tem2!=null)tem2=tem2.next;
	}		
		if(reg==1) {
			tem3.next=new ListNode(reg);              //最后一位溢出
		}
		return l3.next;

    
	}

