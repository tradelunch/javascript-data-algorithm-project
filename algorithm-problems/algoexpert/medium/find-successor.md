# Find Successor



![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 20.59.27.png>)

* n, n

```jsx
// This is an input class. Do not edit.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
    this.parent = null;
  }
}

function findSuccessor(tree, node) {
  const arr = [];
  traverseHelper(tree, node, arr);
  // console.log(arr, node.value);
  for (let i = 0; i < arr.length; i++) {
    if (arr[i].value !== node.value) continue;
    return arr[i + 1];
  }
  
  return null;
}

function traverseHelper(tree, node, arr) {
  if (tree === null) {
    return;
  }
  traverseHelper(tree.left, node, arr);
  arr.push(tree);
  traverseHelper(tree.right, node, arr);
  return;
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.findSuccessor = findSuccessor;
```

* h, 1 ( left node or parent node of right)

```jsx
// This is an input class. Do not edit.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
    this.parent = null;
  }
}

function findSuccessor(tree, node) {
  return find(tree, node);
}

function find(node, target) {

  // check if target has right node;
  if (target.right !== null) {
    // has right then right itself or left most
    let currentNode = target.right;
    while (currentNode.left !== null) {
      currentNode = currentNode.left;
    }
    // has no left? target.right
    // has left? left -> left(this) -> null
    return currentNode;
  }

  // if target has no right
  // then need to check parent
  let currentNode = target;
  while (currentNode.parent !== null) {
    // if currentNode.parent.left === currnetNode
    // its next node to visit is currentNode.parent, and it is a successor
    if (currentNode.parent.left === currentNode) {
      return currentNode.parent;
    }

    currentNode = currentNode.parent;
  }

  return currentNode.parent;
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.findSuccessor = findSuccessor;
```
