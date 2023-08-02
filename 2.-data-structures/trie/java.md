# Java



[LeetCode - The World's Leading Online Programming Learning Platform](https://leetcode.com/problems/word-search-ii/solutions/3835399/java-99-faster-dfs-with-trie/)



```jsx

    private static final class Trie {
        private static final int R = 26;

        private final Trie parent;

        private String word;
        private int counter;
        private char val;

        private final Trie[] nexts = new Trie[R];

        public Trie(Trie parent) {
            this.parent = parent;
        }

        public void add(String s) {
            Trie curr = this;
            for (int i=0; i<s.length(); i++) {
                curr.add(s.charAt(i));
                curr = curr.get(s.charAt(i));
            }
            curr.word = s;
        }

        public void remove(String s) {
            word = null;

            var curr = this;
            for (int i=s.length() - 1; i>=0; i--) {
                curr.counter--;
                var parent = curr.parent;
                if (curr.counter == 0) {
                    parent.nexts[curr.val - 'a'] = null;
                }

                curr = parent;
            }
        }

        public boolean isWord() {
            return word != null;
        }

        public String getWord() {
            return word;
        }

        public void addAll(String[] ss) {
            for (String s : ss) {
                add(s);
            }
        }

        private void add(char c) {
            if (!contains(c)) {
                nexts[c - 'a'] = new Trie(this);
                nexts[c - 'a'].val = c;
            }
            nexts[c - 'a'].counter++;
        }

        private boolean contains(char c) {
            return nexts[c - 'a'] != null
                && nexts[c - 'a'].counter != 0;
        }

        private Trie get(char c) {
            return nexts[c - 'a'];
        }
    }
}
```

```java
```
