# BST Traversal

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 22.47.32.png>)

*

```jsx
function inOrderTraverse(tree, arr) {
  if (tree === null){
    return;
  }

  inOrderTraverse(tree.left, arr);
  arr.push(tree.value);
  inOrderTraverse(tree.right, arr);
  
  return arr;
}

function preOrderTraverse(tree, arr) {
  if (tree === null){
    return;
  }

  arr.push(tree.value);
  preOrderTraverse(tree.left, arr);
  preOrderTraverse(tree.right, arr);
  
  return arr;
}

function postOrderTraverse(tree, arr) {
  if (tree === null){
    return;
  }

  postOrderTraverse(tree.left, arr);
  postOrderTraverse(tree.right, arr);
  arr.push(tree.value);
  
  return arr;
}

// Do not edit the lines below.
exports.inOrderTraverse = inOrderTraverse;
exports.preOrderTraverse = preOrderTraverse;
exports.postOrderTraverse = postOrderTraverse;
```
