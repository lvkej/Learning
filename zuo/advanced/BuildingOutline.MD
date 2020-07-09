    public static class Node{
		public boolean isup;
		public int pos;
		public int height;
		
		public Node(boolean isup,int pos,int height){
			this.isup = isup;
			this.pos = pos;
			this.height = height;
		}
	}
	
	public static class NodeComparator implements Comparator<Node> {
		@Override
		public int compare(Node o1, Node o2) {
			if (o1.pos != o2.pos) {				
				return o1.pos - o2.pos;
			}
			if (o1.isup != o2.isup) {
				return o1.isup ? -1 : 1;
			}
			return 0;
		}
	}
	
	public static List<List<Integer>> buildingOutline(int[][] buildings) {
		Node[] nodes = new Node[2*buildings.length];
		for (int i = 0; i < buildings.length; i++) {							//将buildings中的数据存入nodes中
			nodes[2*i] = new Node(true,buildings[i][0],buildings[i][2]);
			nodes[2*i+1] = new Node(true,buildings[i][1],buildings[i][2]);
		}
		
		Arrays.sort(nodes,new NodeComparator());						//nodes排序
		
		TreeMap<Integer, Integer> htmap = new TreeMap<Integer, Integer>();		//记录i之前存在的最高峰<height,times>
		TreeMap<Integer, Integer> phmap = new TreeMap<Integer, Integer>();		//记录每个pos的最高峰<pos,height>
		
		for (int i = 0; i < nodes.length; i++) {
			
			if(nodes[i].isup) {													//在htmap中记录
				if(htmap.containsKey(nodes[i].height)) {
					htmap.put(nodes[i].height, htmap.get(nodes[i].height)+1);
				}else {
					htmap.put(nodes[i].height, 1);
				}
			}else {
				if(htmap.get(nodes[i].height)==1) {
					htmap.remove(nodes[i].height);
				}else {
					htmap.put(nodes[i].height, htmap.get(nodes[i].height)-1);
				}
			}
			
			if(htmap.isEmpty()) {					//如果htmap为空，最大高度填入0
				phmap.put(nodes[i].pos,0);
			}else {													//不为空，最大高度为lastkey
				phmap.put(nodes[i].pos, htmap.lastKey());
			}
		}
		
		List<List<Integer>> res = new ArrayList<>();
		int start = 0;
		int height = 0;
		for (Entry<Integer, Integer> entry : phmap.entrySet()) {
			int curPosition = entry.getKey();
			int curMaxHeight = entry.getValue();
			if (height != curMaxHeight) {
				if (height != 0) {
					List<Integer> newRecord = new ArrayList<Integer>();
					newRecord.add(start);
					newRecord.add(curPosition);
					newRecord.add(height);
					res.add(newRecord);
				}
				start = curPosition;
				height = curMaxHeight;
			}
		}
		return res;
	}
