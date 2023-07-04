---
description: use Union Find data structure to find a cycle
---

# Detect Cycle with Disjoint-set Union Find

> <mark style="color:blue;">**Note: This method assumes that the graph doesn’t contain any self-loops.**</mark>

\


{% embed url="https://leetcode.com/problems/course-schedule/" %}



{% embed url="https://www.geeksforgeeks.org/introduction-to-disjoint-set-data-structure-or-union-find-algorithm/" %}

{% embed url="https://practice.geeksforgeeks.org/problems/detect-cycle-using-dsu/1" %}



Undirected graph

```javascript

/**
 * @param {number} n
 * @param {number[][]} adj
 * @return {number} 
*/

// with disjoint set
// undirected graph
// no self loop
class Solution {
    detectCycle(n,adj){
       /**
        * n = 5;
        * adj = 
        * [
        *   [ 2, 3, 4 ], 
        *   [ 3 ], 
        *   [ 0, 4 ], 
        *   [ 0, 1 ], 
        *   [ 0, 2 ] 
        * ];
        * 
       */
        //   console.log(n, adj);
       this.parents = [];
       this.ranks = [];
       
       for (let i = 0; i < n; i++) {
           this.createSet(i);
       }
       
       const visited = {};
       
       for (let i = 0; i < n; i++) {
           const here = i;
           const arr = adj[i];
           for (const there of arr) {
            const hasSameRoot = this.unionIfNotConnected(here, there);
            if (!hasSameRoot) {
                visited[there] = here;
                continue;
            }
            
            // hasSameRoot === true
            // check reverse is visited directly, if true, directly connected then ok
            
            // 이전에 there -> here 로 연결된 적이 있나요?
            // 0 -> 1, 1 -> 0 으로 두 번 변경 되는게 정상
            // 2 -> 4로 가는 간선인데 root 가 같은데 4 -> 2 가 존재 하지 않으면? cycle
            const isDirectlyConnected = visited[here] === there; 
            
            // console.log(':: ', here, there, hasSameRoot, visited, isDirectlyConnected);
            
            if (!isDirectlyConnected) {
                return 1;
            }
            
           }
        }
        
        return 0;
    }
    
    createSet(v) {
        this.parents[v] = v;
        this.ranks[v] = 1;
    }
    
    find(v) {
        if (this.parents[v] === undefined) 
            return;
        
        // root found
        let root = v;
        while (root !== this.parents[v]) {
            root = this.parents[v];
        }
        
        // pass compression
        while (root !== v) {
            const newV = this.parents[v];
            this.parents[v] = root;
            v = newV;
        }
        
        return root;
    }
    
    unionIfNotConnected(v1, v2) {
        const root1 = this.parents[v1];
        const root2 = this.parents[v2];
        
        if (root1 === undefined || root2 === undefined) {
            throw new Error('illegal arguments exception');
            return;
        }
        
        if (root1 === root2) {
            return true;
        }
        
        const rank1 = this.ranks[root1];
        const rank2 = this.ranks[root2];
        
        if (rank1 >= rank2) {
            this.parents[root2] = root1;
            this.ranks[root1] += this.ranks[root2];
        } else {
            this.parents[root1] = root2;
            this.ranks[root2] = this.ranks[root1];
        }
        
        return false;
    }
}

```



### Directed Graph

Not possible

Use DFS with <mark style="background-color:green;">3</mark> <mark style="background-color:green;"></mark><mark style="background-color:green;"><mark style="color:purple;background-color:red;">`colors`<mark style="color:purple;background-color:red;"></mark> (<mark style="color:blue;">not visited, visiting in current cycle, visited before</mark>)

