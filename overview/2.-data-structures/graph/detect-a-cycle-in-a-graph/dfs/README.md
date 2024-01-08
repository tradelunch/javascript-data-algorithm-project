# DFS \*

## Undirected Graph

{% embed url="https://www.geeksforgeeks.org/detect-cycle-undirected-graph/" %}
Explanation
{% endembed %}

{% embed url="https://practice.geeksforgeeks.org/problems/detect-cycle-in-an-undirected-graph/1" %}
Problem
{% endembed %}

> from: use this when graph is undirected, can omit when graph is directed

> Time: O(V + E): iter V and then iter E, connected to the V
>
> Space: O(V), V is the number of vertices

<figure><img src="../../../../../.gitbook/assets/Screenshot 2023-06-05 at 13.26.22.png" alt="" width="188"><figcaption></figcaption></figure>



```javascript

// if vertex 0 and 1 are connected then, graph = [ [1], [0] ]

const graph = [
    [1, 4],
    [0, 4, 2, 3],
    [1, 3],
    [1, 4, 2],
    [3, 0, 1]
]; // cycle

const graph = [
    [1, 2],
    [0],
    [0],
]; // no cycle

const State = {
  'WHITE': 0, // not visisted
  'GRAY': 1, // current checking
  'BLACK': 2 // visited
}

function dfsAll(adjs) {
    // console.log(adjs);
    const vertexNum = adjs.length;
    const visited = new Array(vertexNum).fill(State.WHITE);
    
    let componentCnt = 0;
    for (let vertex = 0; vertex < adjs.length; vertex++) {
        if (visited[vertex] !== State.WHITE) continue;

        componentCnt += 1; // check component count
        console.log(`:: vertex ${vertex} is traversing, :: components = ${componentCnt}`);
         
        const flag = dfs(adjs, visited, vertex, vertex);
        
        console.log(`vertex ${vertex} form a cycle? ${flag}`)
        
        if (flag === true) {
            console.log('cycle detected!');
            return true;
        }
    }
    
    return false;
}

function dfs(adjs, visited, here, parent) {
    visited[here] = State.BLACK; // 방문 순간 양방향 소통이 일어나 black
    
    const adj = adjs[here];
    for (const str of adj) {
        const there = Number(str);
        
        // if (visited[there] === State.WHITE) {
        //   const flag = dfs(adjs, visited, there, here);
        //     if (flag === true) 
        //         return true;
        // } else if (parent !== there) {
        //     return true;
        // }
        
        if (parent === there) continue;
        if (visited[there] === State.GRAY) return true; // different        
        if (visited[there] === State.BLACK) return true;
        
        const flag = dfs(adjs, visited, there, here);
        if (flag === true)
            return true;
    }
    visited[here] = BLACK;
    return false;
}

dfsAll(graph);
```

<mark style="color:blue;">Undirected graph는 정점간 연결되면  -> <- 양 방향이기 때문에 black 방문 시 gray 방문과 같으 효과르르 갖는다.</mark>&#x20;

## Directed Graph

{% embed url="https://www.geeksforgeeks.org/detect-cycle-direct-graph-using-colors/" %}

```javascript
function cycleInGraph(edges) {
  
  return detectCycle(edges);
}

const State = {
  'WHITE': 0, // not visisted
  'GRAY': 1, // current checking
  'BLACK': 2 // visited
}

function dfs(adjs, visited, here) {
  visited[here] = State.GRAY;

  const adj = adjs[here];
  for (const str of adj) {
    const there = Number(str);
    
    if (visited[there] === State.Black) 
      continue; // black continue; 일방향이기 때문에 => 양 방향이면 black이면 현재로 넘어온 기억이 있다.
    if (visited[there] === State.GRAY) 
      return true; // gray 현재 싸이클에서 돌고 있을 때만

    const flag = dfs(adjs, visited, there);
    if (flag === true) return true;
  }

  visited[here] = State.BLACK;
  return false;
}

function detectCycle(adjs) {
  const visited = new Array(adjs.length).fill(State.WHITE);

  for (let vertex = 0; vertex < adjs.length; vertex++) {
    const canVisit = visited[vertex] === State.WHITE;
    if (!canVisit) continue;
    
    const flag = dfs(adjs, visited, vertex);
    if (flag === true) 
      return true;
  }

  return false;
}

```

directed graph는 한 방향 이기 때문에 <mark style="color:blue;">balck을 방문해도 괜찮다</mark>
