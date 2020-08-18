    public class MinStack {
    Stack<Integer> min;
    Stack<Integer> help;

    /** initialize your data structure here. */
    public MinStack() {
        min = new Stack<Integer>();
        help = new Stack<Integer>();
    }
    
    public void push(int x) {
        help.push(x);
        if(min.isEmpty()){
            min.push(x);
        }else if(x<min.peek()){
            min.push(x);        
        }else{
            min.push(min.peek());
        }
    }
    
    public void pop() {
        if(help.isEmpty()){
            return;
        }
        help.pop();
        min.pop();
    }
    
    public int top() {
        if(help.isEmpty()){
            return 0;
        }
        return help.peek();
        
    }
    
    public int min() {
        if(help.isEmpty()){
            return 0;
        }
        return min.peek();
    }
}
