# Find Nodes Distance K

![](<../../../.gitbook/assets/Screenshot 2023-02-14 at 22.41.48.png>)

* n, n

```jsx
// This is an input class. Do not edit.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class Solution {
  constructor() {
    this.arr = [];
  }
}

function findNodeToParents(node, nodeToParents, parent = null) {
  if (node === null) return;
  nodeToParents[node.value] = parent;
  findNodeToParents(node.left, nodeToParents, node);
  findNodeToParents(node.right, nodeToParents, node);
}

function findNodesDistanceK(tree, target, k) {
  const ans = new Solution();

  const nodeToParents = {};
  findNodeToParents(tree, nodeToParents, null);
  
  let targetNode = tree;
  if (tree.value !== target) {
    const parent = nodeToParents[target];
    if (parent.left !== null && parent.left.value === target) {
      targetNode = parent.left; 
    } else {
      targetNode = parent.right;
    }
  }

  let q = [[0, targetNode]];

  const set = new Set();
  while (q.length > 0) {
    const [count, currentNode] = q.shift();

    if (set.has(currentNode.value)) continue;
    set.add(currentNode.value);
    
    if (count > k) break;

    if (count < k) {
      const parent = nodeToParents[currentNode.value];
      parent && q.push([count + 1, parent]);
      currentNode.left && q.push([count + 1, currentNode.left]);
      currentNode.right && q.push([count + 1, currentNode.right]);      
      continue;
    }
    ans.arr.push(currentNode.value);
  }
  
  return ans.arr;
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.findNodesDistanceK = findNodesDistanceK;
```
