---
description: 'Disjoint-set: not sharing any element between two sets'
---

# Union Find



{% embed url="https://www.geeksforgeeks.org/introduction-to-disjoint-set-data-structure-or-union-find-algorithm/" %}

{% embed url="https://www.geeksforgeeks.org/union-by-rank-and-path-compression-in-union-find-algorithm/" %}

<figure><img src="../../../.gitbook/assets/Screenshot 2023-06-08 at 12.21.26.png" alt=""><figcaption></figcaption></figure>

```javascript
// Do not edit the class below except for
// the constructor and the createSet, find,
// and union methods. Feel free to add new
// properties and methods to the class.
class UnionFind {
  constructor(n = 0) {
    // Write your code here.
    this.parents = new Array(n);
    this.ranks = new Array(n).fill(1);
  }

  validate(v) {
    if (v < 0 || v >= this.parents.length) {
      throw Error('Illegal Arguments Exception:: Out of Bound');
    }
  }

  createSet(value) {
    if (this.parents[value]) {
      return;
    }

    // this.parents[value] === value :: root
    // root index and value are equal
    this.parents[value] = value;
    return;
  }

  findIter(v) {
    // if not created(initialized)
    if (this.parents[v] === undefined)
      return;

    // root(maybe?)
    let root = v;
    
    // if this root is not a root, find root
    while (root !== this.parents[root]) {
      root = this.parents[root];
    }

    // path compression
    // Root is the root, and then set all child values of the root to root itself.
    // Time complexity of this is O(ɑ(N)) Ackerman
    while (root !== this.parents[v]) {
      const parent = this.paretns[v];
      this.parents[v] = root;
      v = parent; 
    }

    return root;
  }

  find(value) {
    if (this.parents[value] === undefined) {
      return;
    }

    if (this.parents[value] === value) {
      return value;
    }

    const parent = this.parents[value] = this.find(this.parents[value]);
    return parent;
  }

  union(v1, v2) {
    const root1 = this.find(v1);
    const root2 = this.find(v2);

    // if undefined? there is not set for that value, so can not perform union
    if (root1 === undefined || root2 === undefined) {
      return;
    }

    // same root? do nothing
    if (root1 === root2) {
      return;
    }

    // find each root rank
    const rank1 = this.ranks[root1];
    const rank2 = this.ranks[root2];

    // compare each rank, higher rank has higher height
    if (rank1 >= rank2) {
      this.parents[root2] = root1;
      this.ranks[root1] += 1;
    } else {
      this.parents[root1] = root2;
      this.ranks[root2] += 1;
    }
    
    return;
  }
}

// Do not edit the line below.
exports.UnionFind = UnionFind;

```





