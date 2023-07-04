---
description: Edges should have to be n - 1 where n is the number of vertexes
---

# Count edges - undirected only





### Undirected Graph

* only tree possible

```javascript
const edges = [

];

function hasCycle(edges) {
    let count = 0;
    for (let vetex = 0; i < edges.length; vertex++) {
        count += edges[vertex].length;
    }
    
    return Math.floor(count / 2) === edges.length ? true : false;
}

```

### Directed Graph

No. Use DFS

