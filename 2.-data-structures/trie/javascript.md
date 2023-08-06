# Javascript

```javascript

const ALPHABET_SIZE = 26;
class TrieNode {

    constructor(parent, val, level = 0) {
        this.parent = parent;
        this.val = val;
        this.level = level;
        this.children = new Array(ALPHABET_SIZE).fill(null);
    }

}

class Trie {

    constructor(root) {
        this.root = root ?? new TrieNode(null);
        this.isEndOfWord = false;
    }

    insert(s) {
        let currentNode = this.root;

        let idx;
        for (let i = 0; i < s.length; i++) {
            const c = s[i];

            idx = c.charCodeAt() - 'a'.charCodeAt();
            if (currentNode.children[idx] === null) {
                currentNode.children[idx] = new TrieNode(currentNode, c, currentNode.level + 1);
            }

            currentNode = currentNode.children[idx];
        }

        currentNode.isEndOfWord = true;
    }

    search(s) {
        let currentNode = this.root;

        let idx;
        for (let i = 0; i < s.length; i++) {
            const c = s[i];
            idx = c.charCodeAt() - 'a'.charCodeAt();
            if (currentNode.children[idx] == null)
                return false;
            currentNode = currentNode.children[idx];
        }

        return currentNode.isEndOfWord;
    }

    startsWith(s) {
        let currentNode = this.root;

        let idx;
        for (let i = 0; i < s.length; i++) {
            const c = s[i];
            idx = c.charCodeAt() - 'a'.charCodeAt();
            if (currentNode.children[idx] == null)
                return [false, currentNode.isEndOfWord];
            currentNode = currentNode.children[idx];
        }

        return [true, currentNode.isEndOfWord];
    }

    insertAll(arr) {
        for (const s of arr) {
            this.insert(s);
        }
    }


}
```
