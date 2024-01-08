# Youngest Common Ancestor



<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-23 at 21.55.03.png" alt=""><figcaption></figcaption></figure>

* h, h

```jsx
// This is an input class. Do not edit.
class AncestralTree {
  constructor(name) {
    this.name = name;
    this.ancestor = null;
  }
}

function getYoungestCommonAncestor(topAncestor, descendantOne, descendantTwo) {

  const pathOne = hasBAsAncestor(descendantOne, topAncestor);
  const pathTwo = hasBAsAncestor(descendantTwo, topAncestor);

  let idx1 = pathOne.length - 1;
  let idx2 = pathTwo.length - 1;
  while (idx1 >= 0 && idx2 >= 0) {
    if (pathOne[idx1] !== pathTwo[idx2]) break;
    idx1--;
    idx2--;
  }

  return pathOne[idx1 + 1];
}

function hasBAsAncestor(node) {
  const path = [];
  
  let currentNode = node;
  while (currentNode !== null) {
    path.push(currentNode);  
    currentNode = currentNode.ancestor;
  }

  return path;
}

// Do not edit the lines below.
exports.AncestralTree = AncestralTree;
exports.getYoungestCommonAncestor = getYoungestCommonAncestor;
```

* h, 1

```jsx
// This is an input class. Do not edit.
class AncestralTree {
  constructor(name) {
    this.name = name;
    this.ancestor = null;
  }
}

function getYoungestCommonAncestor(topAncestor, descendantOne, descendantTwo) {
  const d1 = findDepth(descendantOne);
  const d2 = findDepth(descendantTwo);

  let diff = Math.abs(d1 - d2);
  if (d1 > d2) {
    while (diff > 0) {
      descendantOne = descendantOne.ancestor;
      diff--;
    }
  } else if (d1 < d2) {
    while (diff > 0) {
      descendantTwo = descendantTwo.ancestor;
      diff--;
    }  
  }

  while (descendantOne !== descendantTwo) {
    descendantOne = descendantOne.ancestor;
    descendantTwo = descendantTwo.ancestor;
  }

  return descendantOne;
}

function findDepth(node) {
  let depth = 0;
  
  let currentNode = node;
  while (currentNode !== null) {
    depth += 1;
    currentNode = currentNode.ancestor
  }

  return depth - 1;
}

// Do not edit the lines below.
exports.AncestralTree = AncestralTree;
exports.getYoungestCommonAncestor = getYoungestCommonAncestor;
```
