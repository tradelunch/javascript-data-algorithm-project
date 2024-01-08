# Validate Bst

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 22.46.50.png>)



*

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

function validateBst(tree) {
  return validateHelper(tree, -Infinity, Infinity)
}

function validateHelper(node, min, max) {
  if (node === null) {
    return true;
  }

  if (node.value < min || node.value >= max) {
    return false;
  }

  const left = validateHelper(node.left, min, node.value);
  const right = validateHelper(node.right, node.value, max);

  return left && right;
}

// Do not edit the line below.
exports.BST = BST;
exports.validateBst = validateBst;
```
