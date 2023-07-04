# Reconstruct Bst

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 19.19.30.png>)



* n, n (need to create n bst nodes)

```jsx
// This is an input class. Do not edit.
class BST {
  constructor(value, left = null, right = null) {
    this.value = value;
    this.left = left;
    this.right = right;
  }
}

class IterIndex {
  constructor(value) {
    this.index = value;
  }
}

function reconstructBst(preOrderTraversalValues) {
  const trace = new IterIndex(0);
  const bst = buildBst(preOrderTraversalValues, trace);
  return bst;
}

function buildBst(arr, trace, min = -Infinity, max = Infinity) {
  if (trace.index >= arr.length) {
    return null;
  }

  const value = arr[trace.index];
  if (value < min || value >= max) 
    return null;

  trace.index += 1;
  const bst = new BST(value);
  bst.left = buildBst(arr, trace, min, value);
  bst.right = buildBst(arr, trace, value, max);

  return bst;
}

// Do not edit the lines below.
exports.BST = BST;
exports.reconstructBst = reconstructBst;
```
