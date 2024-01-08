# Merging LinkedLists





* max(m, n), max(m, n)

```jsx
// This is an input class. Do not edit.
class LinkedList {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

exports.LinkedList = LinkedList;

function mergingLinkedLists(linkedListOne, linkedListTwo) {
  let set = new Set();
  let currentNode = linkedListOne;
  while (currentNode !== null) {
    set.add(currentNode);
    currentNode = currentNode.next;
  }

  currentNode = linkedListTwo;
  while (currentNode !== null) {
    if (set.has(currentNode)) {
      return currentNode;
    }
    currentNode = currentNode.next;
  }
  
  return null;
}

// Do not edit the line below.
exports.mergingLinkedLists = mergingLinkedLists;
```

* max(n, m), 1

```jsx
// This is an input class. Do not edit.
class LinkedList {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

exports.LinkedList = LinkedList;

function mergingLinkedLists(linkedListOne, linkedListTwo) {

  let flag1 = false;
  let flag2 = false;
  
  let node1 = linkedListOne;
  let node2 = linkedListTwo;
  while (node1 !== null || node2 !== null) {
    if (node1 === null) {
      node1 = linkedListTwo;
    }
    if (node2 === null) {
      node2 = linkedListOne;
    }
    if (node1 === node2) return node1;

    node1 = node1.next;
    node2 = node2.next;
  }
  
  return null;
}

// Do not edit the line below.
exports.mergingLinkedLists = mergingLinkedLists;
```
