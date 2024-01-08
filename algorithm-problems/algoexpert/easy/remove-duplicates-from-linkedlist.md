# Remove Duplicates From LinkedList

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 19.07.58.png" alt=""><figcaption></figcaption></figure>

* create prevNode

```jsx
// This is an input class. Do not edit.
class LinkedList {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

function removeDuplicatesFromLinkedList(linkedList) {

  let currentNode = linkedList;
  let prevNode = new LinkedList();
  prevNode.next = currentNode;
  
  while (currentNode !== null) {
    if (prevNode.value !== currentNode.value) {
      prevNode = currentNode;
      currentNode = currentNode.next;
      continue;
    }
    
    prevNode.next = currentNode.next;
    currentNode = currentNode.next;
  }
  
  return linkedList;
}

// Do not edit the lines below.
exports.LinkedList = LinkedList;
exports.removeDuplicatesFromLinkedList = removeDuplicatesFromLinkedList;
```

* find next distinct node

```jsx
// This is an input class. Do not edit.
class LinkedList {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

function removeDuplicatesFromLinkedList(linkedList) {

  let currentNode = linkedList;
  while (currentNode !== null) {
    let nextDistinctNode = currentNode.next;
    while (nextDistinctNode !== null && nextDistinctNode.value === currentNode.value) {
      nextDistinctNode = nextDistinctNode.next;
    }
    
    currentNode.next = nextDistinctNode;
    currentNode = currentNode.next;
  }
  
  return linkedList;
}

// Do not edit the lines below.
exports.LinkedList = LinkedList;
exports.removeDuplicatesFromLinkedList = removeDuplicatesFromLinkedList;
```
