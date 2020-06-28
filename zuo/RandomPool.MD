    public static class Pool<k>{
		private HashMap<k, Integer> keymap;
		private HashMap<Integer,k> indexmap;
		private int size;
		public Pool() {
			this.indexmap = new HashMap<Integer, k>();
			this.keymap = new HashMap<k, Integer>();
			this.size=0;
		}
		
		public void insert(k key) {
			if(!this.keymap.containsKey(key)) {
				this.keymap.put(key, size);
				this.indexmap.put(size++, key);
			}
		}
		public void delete(k key) {
			if(keymap.containsKey(key)) {
				int deleteIndex = this.keymap.get(key);
				int lastIndex = --this.size;
				k lastKey = this.indexmap.get(lastIndex);
				this.keymap.remove(key);
				this.indexmap.remove(lastIndex);
				this.keymap.put(lastKey, deleteIndex);
				this.indexmap.put(deleteIndex, lastKey);
			}
		}
		public k getrandom() {
			if(size==0) {
				return null;
			}
			return indexmap.get((int)(Math.random()*size));
		}
	}
