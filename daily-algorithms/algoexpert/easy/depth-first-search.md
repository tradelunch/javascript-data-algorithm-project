# Depth-first Search

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 18.41.06.png" alt=""><figcaption></figcaption></figure>

```javascript
// Do not edit the class below except
// for the depthFirstSearch method.
// Feel free to add new properties
// and methods to the class.
class Node {
  constructor(name) {
    this.name = name;
    this.children = [];
  }

  addChild(name) {
    this.children.push(new Node(name));
    return this;
  }

  depthFirstSearch(arr) {
    // this.dfsRecursion(this, arr);
    this.dfsIteration(this, arr);
    return arr;
  }
  
  dfsRecursion(node, arr) {
    arr.push(node.name);
    for (const child of node.children) {
      this.dfsRecursion(child, arr);
    }
    
    return arr;
  }

  dfsIteration(node, arr) {
    const q = [node];
    while (q.length > 0) {
      const target = q.pop();

      arr.push(target.name);
      for (let i = target.children.length - 1; i >= 0; i--) {
        q.push(target.children[i]);
      }
      
    }
    
    return arr;
  }


}

// Do not edit the line below.
exports.Node = Node;
```
