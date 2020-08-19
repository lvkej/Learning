   //两种解法，一种利用HashMap，空间复杂度O(N),循环2遍;
	//另一种再每个原节点后添加一个复制节点，空间复杂度O(1),需要循环3遍。
	public class Node{
		int val;
		Node next,random;
		
		Node(int val){
			this.val=val;
			this.next=null;
			this.random=null;
		}
	}
	
	public Node copyRandomList(Node head) {
		HashMap<Node,Node> map = new HashMap<Node,Node>();
		Node cur = head;
		while(cur!=null) {
			map.put(cur, new Node(cur.val));
			cur=cur.next;
		}
		cur=head;
		while(cur!=null) {
			map.get(cur).next=map.get(cur.next);
			map.get(cur).random=map.get(cur.random);
			cur=cur.next;
		}
		return map.get(head);
	}
		
    
    
    
	public Node copyRandomList(Node head) {
        Node cur = head,tmp,next;
        
        while(cur!=null) {									//每个节点后加一个复制节点
        	next=cur.next;
        	tmp=new Node(cur.val);
        	cur.next=tmp;
        	tmp.next=next;
        	cur=next;
        }
        
        cur=head;
        while(cur!=null) {
        	if(cur.random!=null) {							//串联节点间的random
        		cur.next.random=cur.random.next;
        	}
        	
        	cur=cur.next.next;
        }
        
        Node h = new Node(0);
        cur=head;
        while(cur!=null) {									//解耦
        	next=cur.next.next;
        	h.next=cur.next;
        	h=cur.next;
        	cur=next;
        }
        
        return h.next;
    }
