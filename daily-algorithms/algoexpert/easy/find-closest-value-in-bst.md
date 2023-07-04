# Find Closest Value In Bst

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 16.34.26.png" alt=""><figcaption></figcaption></figure>

* use BST min max property

```jsx
function findClosestValueInBst(tree, target) {
  let parentNode = null;
  let currentNode = tree;

  let min = -Infinity;
  let max = Infinity;
  while (currentNode !== null) {
    if (currentNode.value === target) {
      return target;
    } else if (currentNode.value > target) {
      max = currentNode.value;
      currentNode = currentNode.left;
    } else if (currentNode.value < target) {
      min = currentNode.value;
      currentNode = currentNode.right;
    }
  }

  const minDiff = Math.abs(min - target);
  const maxDiff = Math.abs(max - target);

  if (minDiff >= maxDiff) return max;

  return min;
}

// This is the class of the input tree. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

// Do not edit the line below.
exports.findClosestValueInBst = findClosestValueInBst;

```

* use closest every iteration

```jsx
function findClosestValueInBst(tree, target) {
  let closest = tree.value;
  let currentNode = tree;

  while (currentNode !== null) {
    if (Math.abs(target - closest) > Math.abs(target - currentNode.value)) {
      closest = currentNode.value;
    }

    if (target >= currentNode.value) {
      currentNode = currentNode.right;
    } else {
      currentNode = currentNode.left;
    }
  }

  return closest;
}

// This is the class of the input tree. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

// Do not edit the line below.
exports.findClosestValueInBst = findClosestValueInBst;
```
