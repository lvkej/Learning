    class MaxQueue {
		LinkedList<Integer> max;
		LinkedList<Integer> que;
	    public MaxQueue() {
	    	this.max = new LinkedList<Integer>();
	    	this.que = new LinkedList<Integer>();
	    }
	    
	    public int max_value() {
	    	return max.size()==0 ? -1 :max.peekFirst();
	    }
	    
	    public void push_back(int value) {
	    	que.addLast(value);
	    	while(!max.isEmpty()&&max.peekLast()<value) {		//队列中最大值的储存，和stack有区别
	    		max.removeLast();
	    	}
	    	max.addLast(value);
	    }
	    
	    public int pop_front() {
	    	if(max.size()!=0&&que.peekFirst().equals(max.peekFirst())) {
	    		max.removeFirst();
	    	}
	    	return que.size()==0 ? -1 : que.pollFirst();
	    }
	}
