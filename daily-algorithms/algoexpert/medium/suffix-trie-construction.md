# Suffix Trie Construction

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 17.34.16.png>)

* recursive

```tsx
// Do not edit the class below except for the
// populateSuffixTrieFrom and contains methods.
// Feel free to add new properties and methods
// to the class.
class SuffixTrie {
  constructor(string) {
    this.root = {};
    this.endSymbol = '*';
    this.populateSuffixTrieFrom(string);
  }

  // O(n^2) time | O(n^2) space: n is the length of string
  populateSuffixTrieFrom(string, idx = 0) {
    if (idx >= string.length) {
      return this.root;
    }

    let node = this.root;
    for (let i = idx; i < string.length; i++) {
      const c = string[i];
      if (node[c] === undefined) node[c] = {};
      node = node[c];
    }
    node[this.endSymbol] = true;
    
    return this.populateSuffixTrieFrom(string, idx + 1);
  }

  // O(w) time | O(1) space: w is the length of string
  contains(string) {
    let node = this.root;
    for (const c of string) {
      if (node[c] === undefined) return false;
      node = node[c];
    }
    return node[this.endSymbol] === true;
  }

}

// Do not edit the line below.
exports.SuffixTrie = SuffixTrie
```

* iteration

```tsx
  // O(n^2) time | O(n^2) space: n is the length of string
  populateSuffixTrieFrom(string) {

    for (let i = 0; i < string.length; i++) {
	    let node = this.root;
			for (let j = i; j < string.length; j++) {
	      const c = string[j];
	      if (node[c] === undefined) node[c] = {};
	      node = node[c];
			}
	    node[this.endSymbol] = true;
    }
  
    return this.root;
  }
```
