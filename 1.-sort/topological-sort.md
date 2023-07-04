# Topological Sort

## Topological Sort

When you want to sort elements with prerequisites

[\[알고리즘\] 위상 정렬(Topological Sort)이란 - Heee's Development Blog](https://gmlwjd9405.github.io/2018/08/27/algorithm-topological-sort.html)

[Topological Sorting - GeeksforGeeks](https://www.geeksforgeeks.org/topological-sorting/)

> Time: O(V + E), visiting all Vertices + connected edges

> Space: O(V + E) or O(V) if we co not count adjs as a extra space

```jsx
const jobs = [1, 2, 3, 4];
const deps = [
  [1, 2],
  [1, 3],
  [3, 2],
  [4, 2],
  [4, 3]
];
```

```jsx
function topologicalSort(jobs, deps) {

  const incommingEdges = {};
  const adjs = {};
  
  // initialize
  for (const vertex of jobs) {
    incommingEdges[vertex] = 0;
    adjs[vertex] = [];
  }
  
  for (const [here, there] of deps) {
    // counting incomming edges
    incommingEdges[there] += 1;
    // add edge from here to there
    adjs[here].push(there);
  }

  // find vertices with incomming edge count is 0
  const q = [];
  for (const vertex of jobs) {
    if (incommingEdges[vertex] === 0) {
      q.push(vertex);
    } 
  }

  const answer = [];
  while (q.length !== 0) {
    const here = q.shift();
    
    const adj = adjs[here];
    for (const there of adj) {
      if (--incommingEdges[there] === 0) {
        q.push(there);
      }
    }

    // incomming edge count is 0, then add cuz it means there is no Prerequisites left
    answer.push(here);
  }

  return answer.length === jobs.length ? answer : [];
}

exports.topologicalSort = topologicalSort;
```
