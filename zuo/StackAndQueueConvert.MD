    public static class TwoStacksQueue {
		private Stack<Integer> stackpush;
		private Stack<Integer> stackpop;

		public TwoStacksQueue() {
			stackpush = new Stack<Integer>();
			stackpop = new Stack<Integer>();
		}
		
		public void push(int num) {
			stackpush.push(num);
		}
		
		public int poll() {
			if(stackpush.isEmpty()&&stackpop.isEmpty()) {
				throw new RuntimeException("Queue is empty!");
			}else if(stackpop.isEmpty()) {                        //先确认pop是否为空，不空不能倒
				while(!stackpush.isEmpty()) {                     //一倒就要倒完
					stackpop.push(stackpush.pop());
				}
			}
			return stackpop.pop();
		}
		
		public int peek() {
			if(stackpush.isEmpty()&&stackpop.isEmpty()) {
				throw new RuntimeException("Queue is empty!");
			}else if(stackpop.isEmpty()) {                        
				while(!stackpush.isEmpty()) {                     
					stackpop.push(stackpush.pop());
				}
			}
			return stackpop.peek();                         //和poll的区别就是peek       
		}


	}

	public static class TwoQueuesStack {
		private Queue<Integer> queue;
		private Queue<Integer> help;
		
		
		public TwoQueuesStack() {
			queue = new LinkedList<Integer>();
			help = new LinkedList<Integer>();
		}

		public void push(int num) {
			queue.add(num);
		}
		
		public int pop() {
			if(queue.isEmpty()) {
				throw new RuntimeException("Stack is empty!");
			}
			while(queue.size()!=1) {
				help.add(queue.poll());
			}
			int res = queue.poll();
			swap();
			return res;
		}
		
		public int peek() {
			if(queue.isEmpty()) {
				throw new RuntimeException("Stack is empty!");
			}
			while(queue.size()!=1) {
				help.add(queue.poll());
			}
			int res = queue.poll();
			help.add(res);
			swap();			
			return res;
		}
		
		private void swap() {
			Queue<Integer> tmp = help;
			help = queue;
			queue = tmp;
		}
		

	}
