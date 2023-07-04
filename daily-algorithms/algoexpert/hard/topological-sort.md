# Topological Sort

![](<../../../.gitbook/assets/Screenshot 2023-02-18 at 19.21.02.png>)

* j + d, j +d
* v +e, v+e

```jsx
function topologicalSort(jobs, deps) {
  const answer = [];
  // create adj list for each job
  const adj = {};
  for (let i = 0; i < jobs.length; i++) {
    const job = jobs[i];
    if (adj[job] === undefined) 
      adj[job] = [];
  }
  
  // form a adj list
  // count edges directing there
  const inCommingEdges = {};
  for (let i = 0; i < deps.length; i++) {
    const [here, there] = deps[i];
    adj[here].push(there);
    
    if (inCommingEdges[there] === undefined) 
      inCommingEdges[there] = 0;
    inCommingEdges[there] += 1;
  }

  // pick all edges, which has no incomming edges
  const q = [];
  for (const [here, edges] of Object.entries(adj)) {
    if (inCommingEdges[here] > 0) continue;
    q.push(here);
  }

  // use bfs to search toplogical sort
  while (q.length > 0) {
    const here = q.shift();
    for (const there of adj[here]) {
      inCommingEdges[there]--;
      if (inCommingEdges[there] > 0) continue;
      q.push(there);
    }
    answer.push(here);
  }

  console.log({
    answer
  });
  
  return answer.length === jobs.length ? answer : [];
}

// not working with dfs
// function dfs(adj, visited, here, order) {
//   visited[here] = 1;
  
//   for (let i = 0; i < adj[here].length; i++) {
//     const there = adj[here][i];
//     if (visited[there] !== 0) continue;

//     // if (visited[there] === 1) continue;
//     dfs(adj, visited, there, order);
//   }
  
//   visited[here] = 2;
// }
// Do not edit the line below.
exports.topologicalSort = topologicalSort;
```
