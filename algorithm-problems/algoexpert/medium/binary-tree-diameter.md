# Binary Tree Diameter

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 20.26.00.png>)

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

class Diameter {
  constructor() {
    this.max = 0;
  }
}

function binaryTreeDiameter(tree) {
  const diameter = new Diameter();
  findDiameter(tree, diameter, 0);
  return diameter.max
}

function findDiameter(node, diameter, height) {
  if (node === null) {
    return 0;
  }

  const left = findDiameter(node.left, diameter);
  const right = findDiameter(node.right, diameter);

  const currentHeight = Math.max(left, right);
  const sumOfHeight = left + right;

  diameter.max = Math.max(diameter.max, sumOfHeight);

  return currentHeight + 1;
}

// Do not edit the line below.
exports.binaryTreeDiameter = binaryTreeDiameter;
exports.BinaryTree = BinaryTree;
```
