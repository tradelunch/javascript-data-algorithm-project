---
description: Edge, Union Find
---

# Kruskal's Algorithm: undirected

{% embed url="https://ongveloper.tistory.com/376" %}
theory
{% endembed %}

{% embed url="https://www.algoexpert.io/questions/kruskals-algorithm" %}
problem
{% endembed %}



<figure><img src="../../.gitbook/assets/Screenshot 2023-06-06 at 14.17.43.png" alt=""><figcaption></figcaption></figure>

```javascript

function kruskalsAlgorithm(edges) {
  // [
  //   [[there vertex, weight], ...]
  //   ...
  //   ...
  //   ...
  // ]

  // parse edges to weight-edge
  const weightedEdges = [];
  for (let here = 0; here < edges.length; here++) {
    const adj = edges[here];
    for (const [there, weight] of adj) {
      weightedEdges.push([weight, [here, there]]);
    }
  }

  // sort weight asc 
  weightedEdges.sort((a, b) => a[0] - b[0]);

  const answer = [];
  
  // iter sorted edges with UnionFind
  // connect if not conneted
  const uf = new UnionFind();

  for (let i = 0; i < weightedEdges.length; i++) {
    const [weight, [here, there]] = weightedEdges[i];
    uf.createSet(here);
    uf.createSet(there);
    const flag = uf.union(here, there);
    if (flag) {
      answer[here] = answer[here] ?? [];
      answer[here].push([there, weight]);

      answer[there] = answer[there] ?? [];
      answer[there].push([here, weight]);
    }
  }
  
  return answer;
}

class UnionFind {
  constructor() {
    this.parents = [];
    this.ranks = [];
  }

  createSet(v) {
    if (this.parents[v] !== undefined) 
      return false;
    
    this.parents[v] = v;
    return true;
  }

  find(v) {
    if (this.parents[v] === v) 
      return v;
    return this.parents[v] = this.find(this.parents[v]);
  }

  union(v1, v2) {
    const root1 = this.find(v1);
    const root2 = this.find(v2);

    if (root1 === root2) return false;

    const rank1 = this.ranks[root1] ?? 1;
    const rank2 = this.ranks[root2] ?? 1;

    if (rank1 >= rank2) {
      this.parents[root2] = root1;
      this.ranks[root1] += 1;
    } else {
      this.parents[root1] = root2;
      this.ranks[root2] += 1;
    }

    return true;
    
  }
  
  
}

// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;

```

