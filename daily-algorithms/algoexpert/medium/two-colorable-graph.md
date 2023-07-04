# Two Colorable - Graph

![](<../../../.gitbook/assets/Screenshot 2023-01-24 at 0.51.21.png>)

* V + E, V

```jsx
let canColor;

function twoColorable(edges) {
  canColor = true;
  bfsAll(edges);
  return canColor;
}

function bfsAll(adjacencyList) {
  const colors = new Array(adjacencyList.length).fill(0);

  let components = 0;
  for (let i = 0; i <= adjacencyList.length; i++) {
    if (colors[i] !== 0) continue;

    components += 1;
    const vertex = i;
    colors[vertex] = components % 2 + 1; // extra work
    
    bfs(adjacencyList, vertex, colors);
  }
}

function bfs(adjacencyList, here, colors) {

  const q = [here];
  while (q.length > 0) {
    const here = q.shift();
    const hereColor = colors[here];
    const edges = adjacencyList[here];
    
    for (let i = 0; i < edges.length; i++) {
      const there = edges[i];
      if (hereColor === colors[there]) {
        canColor = false;
        return;
      }

      if (colors[there] !== 0) continue;
      colors[there] = hereColor === 1 ? 2 : 1;
      q.push(there);
    }
    
  }
}

// Do not edit the line below.
exports.twoColorable = twoColorable;
```
