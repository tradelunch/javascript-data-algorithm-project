# BST Construction

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 21.49.25.png>)

```jsx
// Do not edit the class below except for
// the insert, contains, and remove methods.
// Feel free to add new properties and methods
// to the class.
class BST {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }

  insert(value) {
    let currentNode = this;
    
    while (true) {
      if (currentNode.value <= value) {
        if (currentNode.right !== null) {
          currentNode = currentNode.right;
          continue;
        }
        currentNode.right = new BST(value);
        break;
      } else if (currentNode.value > value) {
        if (currentNode.left !== null) {
          currentNode = currentNode.left;
          continue;
        }
        currentNode.left = new BST(value);
        break;
      }
    }
    
    return this;
  }

  contains(value) {
    let currentNode = this;
    while (currentNode !== null) {
      if (currentNode.value === value) {
        return true;
      } else if (currentNode.value > value) {
        currentNode = currentNode.left;
      } else if (currentNode.value < value) {
        currentNode = currentNode.right;
      }
    }

    return false;
  }

  remove(value, parentNode = null) {
    let currentNode = this;
    while (currentNode !== null) {
      if (currentNode.value > value) {
        parentNode = currentNode;
        currentNode = currentNode.left;
      } else if (currentNode.value < value) {
        parentNode = currentNode;
        currentNode = currentNode.right;
      } else if (currentNode.value === value) {
        if (currentNode.right !== null && currentNode.left !== null) {
          currentNode.value = currentNode.right.getMinValue();
          currentNode.right.remove(currentNode.value, currentNode);
        } else if (parentNode === null) {
          if (currentNode.left !== null) {
            currentNode.value = currentNode.left.value;
            currentNode.right = currentNode.left.right;
            currentNode.left = currentNode.left.left;
          } else if (currentNode.right !== null) {
            currentNode.value = currentNode.right.value;
            currentNode.left = currentNode.right.left;
            currentNode.right = currentNode.right.right;
          } else {
            // ??
          }
      
        } else if (parentNode.left === currentNode) {
          parentNode.left =  currentNode.left !== null ? currentNode.left : currentNode.right;
        } else if (parentNode.right === currentNode) {
          parentNode.right =  currentNode.left !== null ? currentNode.left : currentNode.right;
        }
        break;
      }      
    }

    return this;
  }

  getMinValue() {
    let currentNode = this;
    while (currentNode.left !== null) {
      currentNode = currentNode.left;
    }
    return currentNode.value;
  } 
}

// Do not edit the line below.
exports.BST = BST;
```
