    public class CQueue {
	Stack<Integer> in ;
	Stack<Integer> out;
	public CQueue() {
		in = new Stack<Integer>();
		out = new Stack<Integer>();
    }
    
    public void appendTail(int value) {
    	in.push(value);
    }
    
    public int deleteHead() {
    	if(in.isEmpty()&&out.isEmpty()) {
    		return -1;
    	}
    	if(out.isEmpty()) {
    		while(!in.isEmpty()) {
    			out.push(in.pop());
    		}
    	}
    	return out.pop();
    }
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub
	
	}

}
