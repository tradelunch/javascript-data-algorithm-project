# Validate Three Nodes

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 19.08.38.png>)

* h, h
* recursive

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

function validateThreeNodes(nodeOne, nodeTwo, nodeThree) {
  const isNodeOneAncestor = isAncester(nodeOne, nodeTwo);
  
  if (isNodeOneAncestor) {
    return isAncester(nodeTwo, nodeThree);
  }
  
  const isNodeThreeAncestor = isAncester(nodeThree, nodeTwo);
  if (isNodeThreeAncestor) {
    return isAncester(nodeTwo, nodeOne);
  }

  return false;
}

function isAncester(node1, node2) {
  if (node1 === null) {
    return false;
  }

  if (node1 === node2) return true;

  const left = isAncester(node1.left, node2);
  const right = isAncester(node1.right, node2);

  return left || right;
}

// Do not edit the lines below.
exports.BST = BST;
exports.validateThreeNodes = validateThreeNodes;
```

* h, 1
* iteration

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

function validateThreeNodes(nodeOne, nodeTwo, nodeThree) {
  const isNodeOneAncestor = isAncester(nodeOne, nodeTwo);
  
  if (isNodeOneAncestor) {
    return isAncester(nodeTwo, nodeThree);
  }
  
  const isNodeThreeAncestor = isAncester(nodeThree, nodeTwo);
  if (isNodeThreeAncestor) {
    return isAncester(nodeTwo, nodeOne);
  }

  return false;
}

function isAncester(node1, node2) {
  let currentNode = node1;
  while (currentNode !== null) {
    if (currentNode === node2) return true;
    
    if (currentNode.value > node2.value) {
      currentNode = currentNode.left;
      continue;
    }
    
    currentNode = currentNode.right;
  }

  return false;
}

// Do not edit the lines below.
exports.BST = BST;
exports.validateThreeNodes = validateThreeNodes;
```

* optmized
* d, 1 (d is distance between nodeOne and nodeTwo)

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

function validateThreeNodes(nodeOne, nodeTwo, nodeThree) {

  let search1 = nodeOne;
  let search3 = nodeThree;
  
  while (true) {
    const found3From1 = search1 === nodeThree;
    const found1From3 = search3 === nodeOne;
    const foundNode2 = search1 === nodeTwo || search3 === nodeTwo;
    const finished = search1 === null && search3 === null;

    if (found1From3 || found3From1 || foundNode2 || finished) break;

    if (search1 !== null) {
      search1 = search1.value > nodeTwo.value ? search1.left : search1.right;
    }
    if (search3 !== null) {
      search3 = search3.value > nodeTwo.value ? search3.left : search3.right;
    }
  }

  const is13equal = search1 === nodeThree || search3 === nodeOne;
  const didNotFindNodeTwo = search1 !== nodeTwo && search3 !== nodeTwo;
  if (is13equal || didNotFindNodeTwo) return false;

  return isAncester(nodeTwo, search1 === nodeTwo ? nodeThree : nodeOne)
}

function isAncester(node1, node2) {
  let currentNode = node1;
  while (currentNode !== null) {
    if (currentNode === node2) return true;
    
    if (currentNode.value > node2.value) {
      currentNode = currentNode.left;
      continue;
    }
    
    currentNode = currentNode.right;
  }

  return false;
}

// Do not edit the lines below.
exports.BST = BST;
exports.validateThreeNodes = validateThreeNodes;
```
