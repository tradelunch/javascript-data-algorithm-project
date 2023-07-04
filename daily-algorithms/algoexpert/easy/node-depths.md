# Node Depths

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 18.30.46.png" alt=""><figcaption></figcaption></figure>

```javascript
class DepthSum {
  constructor() {
    this.sum = 0;
  }
}

function nodeDepths(root) {
  const memo = new DepthSum();
  findNodeDepthSum(root, memo)
  return memo.sum;
}

function findNodeDepthSum(node, memo, depth = 0) {
  if (node === null) {
    // return depth;
    return;
  }

  memo.sum += depth;

  const left = findNodeDepthSum(node.left, memo, depth + 1);
  const right = findNodeDepthSum(node.right, memo, depth + 1);

  // return left + right;
  return;
}

// This is the class of the input binary tree.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

// Do not edit the line below.
exports.nodeDepths = nodeDepths;
```
