# Height Balanced Binary Tree



![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 21.40.33.png>)

* n, h

```jsx
// This is an input class. Do not edit.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

function heightBalancedBinaryTree(node) {
  const [flag, height] = checkBalance(node);
  
  return flag;
}

function checkBalance(node) {
  if (node === null) {
    return [true, 0];
  }

  const left = checkBalance(node.left);
  const right = checkBalance(node.right);

  const diff = Math.abs(left[1] - right[1]);
  
  return [left[0] && right[0] && diff <= 1, Math.max(left[1], right[1]) + 1];
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.heightBalancedBinaryTree = heightBalancedBinaryTree;
```
