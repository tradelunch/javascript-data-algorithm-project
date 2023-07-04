---
description: Tree, MST (Kruskal)
---

# Union Find: Disjoint Set



Disjoint-set: 상호 배타적인 부분 집합 => 공통 원소가 없는 집합들을 표현하기 위해 만들어 졌다

> 공통 원소가 없는, 즉 "상호 배타적" 인 부분 집합 들로 나눠진 원소들에 대한 정보를 저장하고 조작하는 자료구조

> The Union-Find algorithm is typically used for problems related to disjoint sets, such as determining if two nodes belong to the same set or not, and merging two sets into one. It's a very efficient algorithm for these types of problems.



## Structure

<pre class="language-javascript"><code class="lang-javascript"><strong>class UnionFind {
</strong>    tracking: number[]; // 
    weights: number[]; // how tall the tree is 
    constructor();
    createSet(v: number);
    find(v: number): number; // return root of v
    union(v1, v2): void; // 
}
</code></pre>



## Implementation

```javascript
// Do not edit the class below except for
// the constructor and the createSet, find,
// and union methods. Feel free to add new
// properties and methods to the class.
class UnionFind {
  constructor() {
    // Write your code here.
    this.parents = [];
    this.weights = [];
  }

  createSet(value) {
    this.parents[value] = value;
    this.weights[value] = 1;
  }

  find(value) {
    if (this.parents[value] === undefined) return null;
    if (this.parents[value] === value) return value;

    return this.parents[value] = this.find(this.parents[value]);
  }

  union(valueOne, valueTwo) {
    const root1 = this.find(valueOne);
    const root2 = this.find(valueTwo);

    if (root1 === null || root2 === null) return;
    if (root1 === root2) return;

    const weight1 = this.weights[root1];
    const weight2 = this.weights[root2];

    if (weight1 === weight2) {
      this.parents[root1] = root2;
      this.weights[root1] += 1;
    } else if (weight1 > weight2) {
      this.parents[root2] = root1;
      this.weights[root2] += 1;
    } else {
      this.parents[root1] = root2;
      this.weights[root1] += 1;
    }
    
    return;
  }
}

// Do not edit the line below.
exports.UnionFind = UnionFind;

```



### reference

{% embed url="https://www.algoexpert.io/questions/union-find" %}

{% embed url="https://ongveloper.tistory.com/376" %}

{% embed url="https://bowbowbow.tistory.com/26" %}

