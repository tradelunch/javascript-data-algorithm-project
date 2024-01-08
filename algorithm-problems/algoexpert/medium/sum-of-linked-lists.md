# Sum Of Linked Lists -

![](<../../../.gitbook/assets/Screenshot 2023-01-24 at 19.34.10.png>)



* min(n, m), min(n, m)

```jsx
// This is an input class. Do not edit.
class LinkedList {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

function sumOfLinkedLists(linkedListOne, linkedListTwo) {
  let node = new LinkedList(0);
  const prevNode = node;

  let carry = 0;
  let currentNode1 = linkedListOne;
  let currentNode2 = linkedListTwo;
  while (currentNode1 !== null || currentNode2 !== null || carry !== 0) {
    let sum = carry;
    currentNode1 !== null && (sum += currentNode1.value);
    currentNode2 !== null && (sum += currentNode2.value);

    carry = Math.floor(sum / 10);
    
    node.next = new LinkedList(sum % 10);
    node = node.next;
    
    currentNode1 = currentNode1 === null ? null : currentNode1.next;
    currentNode2 = currentNode2 === null ? null : currentNode2.next;
  }
    
  return prevNode.next;
}

// Do not edit the lines below.
exports.LinkedList = LinkedList;
exports.sumOfLinkedLists = sumOfLinkedLists;
```
