# Find Kth Largest Value In Bst

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 19.14.30.png>)



* h + k, h

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class Memo {
  constructor() {
    this.count = 0;
    this.value;
  }
}

function findKthLargestValueInBst(tree, k) {
  const memo = new Memo();
  findValue(tree, k, memo);
  return memo.value;
}

function findValue(node, k, memo) {
  if (node === null || memo.value !== undefined) {
    return;
  }

  const right = findValue(node.right, k, memo);
  memo.count += 1;
  if (memo.count === k)
    memo.value = node.value;
  
  const left = findValue(node.left, k, memo);
  
  return;
}

// Do not edit the lines below.
exports.BST = BST;
exports.findKthLargestValueInBst = findKthLargestValueInBst;
```
