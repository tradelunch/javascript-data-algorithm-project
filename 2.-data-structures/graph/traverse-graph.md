# Traverse Graph

## Directed Graph



## Undirected Graph

### Using visited array

```javascript
const graph = [

];

function dfs(adjs, visited, here) {
    visited[here] = true;
    
    const adj = adjs[here];
    for (const there of adj) {
        if (visited[there] === true)
            continue;
        dfs(adjs, visited, there);
    }
    
}

dfs(adjs, 0, 0);
```

### With previous Vertex: When graph is Tree

```javascript

const graph = [

];

function dfs(adjs, from, here) {
    
    const adj = adjs[here];
    for (const there of adj) {
        if (from === there) 
            continue;
        dfs(adjs, here, there);
    }
}

dfs(adjs, 0, 0);
```

