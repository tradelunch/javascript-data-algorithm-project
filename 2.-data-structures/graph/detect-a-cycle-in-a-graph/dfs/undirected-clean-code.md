# undirected clean code

```javascript
class Solution {
    // Function to detect cycle in an undirected graph.
    isCycle(V, adj) {
        const flag = dfsAll(adj);
        return flag ? 1 : 0;
    }
}

function dfsAll(adjs) {
    // console.log(adjs);
    const vertexNum = adjs.length;
    const visited = new Array(vertexNum).fill(false);
    
    for (let vertex = 0; vertex < adjs.length; vertex++) {
        if (visited[vertex] === true) continue;
        const flag = dfs(adjs, visited, vertex, -1);
        
        if (flag === true) {
            return true;
        }
    }
    
    return false;
}

function dfs(adjs, visited, here, parent) {
    visited[here] = true;
    
    const adj = adjs[here];
    for (const str of adj) {
        const there = Number(str);
        
        if (parent === there) continue;
        if (visited[there] === true) return true;
        
        const flag = dfs(adjs, visited, there, here);
        
        if (flag === true)
            return true;
    }

    return false;
}
```
