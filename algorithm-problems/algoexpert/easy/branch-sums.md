# Branch Sums

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 17.54.53.png" alt=""><figcaption></figcaption></figure>

```jsx
// This is the class of the input root.
// Do not edit it.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BranchSums {
  constructor() {
    this.sums = [];
  }
}

function branchSums(root) {
  const memo = new BranchSums();
  findBranchSums(root, memo);
  return memo.sums;
}

function findBranchSums(node, memo, sum = 0) {
  if (node === null) {
    return;
  }
  
  sum += node.value;
  if (node.left === null && node.right === null) {
    memo.sums.push(sum);
  }
  
  const left = findBranchSums(node.left, memo, sum);
  const right = findBranchSums(node.right, memo, sum);

  return;
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.branchSums = branchSums;
```
