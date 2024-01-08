# Invert Binary Tree

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 20.17.41.png>)

* n, n

```jsx
function invertBinaryTree(tree) {
  return invertHelper(tree);
}

function invertHelper(node) {
  if (node === null) {
    return null;
  }

  const left = node.left;
  const right = node.right;

  node.right = invertHelper(node.left); 
  // can not use node.right cuz you loose your reference from above
  node.left = invertHelper(right); 

  return node;
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
exports.invertBinaryTree = invertBinaryTree;
```
