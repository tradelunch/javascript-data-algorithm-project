# Breadth First Search

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 21.07.57.png>)

* V + E, V

```jsx
// Do not edit the class below except
// for the breadthFirstSearch method.
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

  breadthFirstSearch(arr) {
    const q = [this];
    while (q.length > 0) {
      const node = q.shift();

      for (const child of node.children) {
        q.push(child);
      }

      arr.push(node.name);
      node.visited = true;
    }
    
    return arr;
  }
}

// Do not edit the line below.
exports.Node = Node;
```
