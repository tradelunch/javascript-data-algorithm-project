# Cycle in Graph -

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 22.58.12.png>)

* just checking there is a cycle

```jsx
/*
0: white => not yet
1: grey => in traversing a graph
2: black => completed
*/

function cycleInGraph(edges) {
  const hasCycle = dfsAll(edges);
  
  return hasCycle;
}

function dfsAll(adjacencyList) {
  const visited = new Array(adjacencyList.length).fill(0);
  
  for (let i = 0; i < adjacencyList.length; i++) {
    const vertex = i;
    if (visited[vertex] !== 0) continue;
    if (visited[vertex] === 2) continue; 
		// either is fine
    
    const hasCycle = dfs(adjacencyList, vertex, visited);
    console.log({
      visited
    })
    if (hasCycle === true) return true;
  }
  
  return false;
}

function dfs(adjacencyList, here, visited) {
  visited[here] = 1;

  const edges = adjacencyList[here];
  for (let i = 0; i < edges.length; i++) {
    const there = edges[i];
    
    if (visited[there] === 1) return true;
    if (visited[there] === 2) continue;
    const hasCycle = dfs(adjacencyList, there, visited);
    if (hasCycle === true) return true;
  }

  visited[here] = 2;
  return false;
}

// Do not edit the line below.
exports.cycleInGraph = cycleInGraph;
```

```jsx
// traverse short
function dfs(adjacencyList, here, visited) {
  visited[here] = 1;

  const edges = adjacencyList[here];
  for (let i = 0; i < edges.length; i++) {
    const there = edges[i];
    
    if (visited[there] === 1) return true;
    if (visited[there] === 2) continue;
    const hasCycle = dfs(adjacencyList, there, visited);
    if (hasCycle === true) return true;
  }

  visited[here] = 2;
  return false;
}
// traverse more than above
function dfs(adjacencyList, here, visited) {
  visited[here] = 1;

	let hasCycle = false;
  const edges = adjacencyList[here];
  for (let i = 0; i < edges.length; i++) {
    const there = edges[i];
    
    if (visited[there] === 1) return true;
    if (visited[there] === 2) continue;
    hasCycle = dfs(adjacencyList, there, visited);
  }

  visited[here] = 2;
  return hasCycle;
}
```

* v + e, v
* with everything

```jsx
/*
0: white => not yet
1: grey => in traversing a graph
2: black => completed
*/

let hasCycle = false;
function cycleInGraph(edges) {
  hasCycle = false;
  dfsAll(edges);
  
  return hasCycle;
}

function dfsAll(adjacencyList) {
  const totalVisited = new Array(adjacencyList.length).fill(0);
  
  let howManyComponents = 0;
  for (let i = 0; i < adjacencyList.length; i++) {
    const vertex = i;
    
    if (totalVisited[vertex] !== 0) continue; // if it is 1, then error
    howManyComponents += 1;
    
    const visited = new Array(adjacencyList.length).fill(0);
    dfs(adjacencyList, vertex, totalVisited, visited);
  }

  console.log({
    howManyComponents,
    totalVisited,
    hasCycle
  })
}

function dfs(adjacencyList, here, totalVisited, visited) {

  totalVisited[here] = 1;
  visited[here] = 1;

  const edges = adjacencyList[here];
  for (let i = 0; i < edges.length; i++) {
    const there = edges[i];
    if (visited[there] === 1) {
      hasCycle = true;
      // return;
      break;
    }

    if (visited[there] === 2) continue;

    dfs(adjacencyList, there, totalVisited, visited);
  }

  totalVisited[here] = 2;
  visited[here] = 2;
}

// Do not edit the line below.
exports.cycleInGraph = cycleInGraph;
```
