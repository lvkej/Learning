    public static class MyStack2 {
		private Stack<Integer> stackdata;           //两个栈
		private Stack<Integer> stackmin;
		
		
		public MyStack2() {
			this.stackdata = new Stack<Integer>();
			this.stackmin = new Stack<Integer>();
		}

		public void push(int num) {
			if(stackmin.isEmpty()) {
				stackmin.push(num);
			}else if(num<this.getmin()) {
				stackmin.push(num);                         //如果新数比栈顶的小就压入
			}else {
				stackmin.push(stackmin.peek());             //如果新数比栈顶的大就压入栈顶的数    
			}
			stackdata.push(num);
		}
		
		public int pop() {
			if(stackdata.isEmpty()) {
				throw new RuntimeException("Your stack is empty.");
			}
			stackmin.pop();
			return stackdata.pop();
		}
		
		public int getmin() {
			if(stackdata.isEmpty()) {
				throw new RuntimeException("Your stack is empty.");
			}
			return stackmin.peek();                 //输出栈顶的数
		}
		

	}
