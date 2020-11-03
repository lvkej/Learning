    public static boolean isValid(String s) {

        char[] chs = s.toCharArray();
        Stack<Character> stack = new Stack<Character>();
        int index = 0;
        char tmp;
        stack.push(chs[index++]);
        while (index < chs.length) {

            tmp = get(stack.peek());
            if (tmp == '=') {
                return false;
            } else if (tmp == chs[index]) {
                stack.pop();
                index++;
            } else {
                stack.push(chs[index++]);
                continue;
            }
            if (stack.isEmpty()&&index < chs.length) {
                stack.push(chs[index++]);
            }
        }
        return stack.isEmpty() ? true : false;

    }

    public static char get(char c) {
        if (c == '(') {
            return ')';
        } else if (c == '{') {
            return '}';
        } else if (c == '[') {
            return ']';
        } else {
            return '=';
        }
    }
    --------------------------------------------------
      public boolean isValid(String s) {
        int n = s.length();
        if (n % 2 == 1) {
            return false;
        }

        Map<Character, Character> pairs = new HashMap<Character, Character>() {{
            put(')', '(');
            put(']', '[');
            put('}', '{');
        }};
        Deque<Character> stack = new LinkedList<Character>();
        for (int i = 0; i < n; i++) {
            char ch = s.charAt(i);
            if (pairs.containsKey(ch)) {
                if (stack.isEmpty() || stack.peek() != pairs.get(ch)) {
                    return false;
                }
                stack.pop();
            } else {
                stack.push(ch);
            }
        }
        return stack.isEmpty();
    }

