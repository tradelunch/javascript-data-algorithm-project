# Kruskal’s algorithm vs Prim’s algorithm

<figure><img src="../../../.gitbook/assets/Screenshot 2023-02-19 at 19.13.17.png" alt=""><figcaption></figcaption></figure>

* ElogE, E + V

```jsx
function kruskalsAlgorithm(edges) {
  // create arr to store edge
  const weightEdges = [];
  for (let i = 0; i < edges.length; i++) {
    const here = i;
    for (const [there, weight] of edges[here]) {
      weightEdges.push([here, there, weight]);
    }
  }

  // sort arr asc depending on edge weight
  weightEdges.sort((a, b) => a[2] - b[2]);

  // crate union find
  const uf = new UnionFind(edges.length);
  // create mst to find 
  const mst = edges.map(a => []);
  for (let i = 0; i < weightEdges.length; i++) {
    const [here, there, weight] = weightEdges[i];
    if (uf.find(here) === uf.find(there)) continue;
    mst[here].push([there, weight]);
    mst[there].push([here, weight]);
    uf.union(here, there);
  }
  
  return mst;
}

class UnionFind {
  constructor(size) {
    this.arr = new Array(size);
    for (let i = 0; i < size; i++) {
      this.arr[i] = i;
    }
    this.weights = new Array(size).fill(0);
  }
  

  create(a) {
    return this.arr[a] = a;
  }

  find(value) {
    if (value === undefined) 
      return null;

    if (this.arr[value] === value)
      return value;

    return this.arr[value] = this.find(this.arr[value]);
  }

  union(a, b) {
    const rootA = this.find(a);
    const rootB = this.find(b);
    if (rootA === rootB) return;
    
    if (this.weights[rootA] > this.weights[rootB]) {
      this.arr[rootB] = rootA;
      this.weights[rootA]++;
    } else {
      this.arr[rootA] = rootB;
      this.weights[rootB]++;
    }
    
    return;
  }
  
}

// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;
```

* ElogV, V + E

```jsx
function kruskalsAlgorithm(edges) {
  // create min heap with comparator;
  const minHeap = new MinHeap([], (a, b) => a[0] - b[0] > 0 ? false : true);
  
  const mst = edges.map(_ => []);
  const tracking = new Set();

  // iterate edges in case all vertices not connected
  for (let i = 0; i < edges.length; i++) {
    
    // pick random vertex
    for (const [there, weight] of edges[i]) {
      minHeap.insert([weight, i, there]);
    }
    tracking.add(i);

    // connect all vertices from random pick
    while (minHeap.heap.length > 0) {
      // console.log({
      //   heap: minHeap.heap, 
      //   tracking,
      //   mst
      // });
      
      // take min vertex;
      const [weight, here, there] = minHeap.remove();
  
      // check new vertex alreay connected
      if (tracking.has(there)) continue;
  
      // add element to mst
      mst[here].push([there, weight]);
      mst[there].push([here, weight]);
  
      // add candidate vertices to min heap
      const adj = edges[there];
      for (const [next, weight] of adj) {
        minHeap.insert([weight, there, next]);
      }
      tracking.add(there);
      
    }
  }
  
  // iterate vertex

  return mst;
}

// Do not edit the class below except for the buildHeap,
// siftDown, siftUp, peek, remove, and insert methods.
// Feel free to add new properties and methods to the class.
class MinHeap {
  constructor(arr, comparator = (a, b) => a - b > 0 ? false : true) {
    this.comparator = comparator;
    // if (this.comparator === undefined) {
    //   this.comparator = function (a, b) {
    //     return a - b > 0 ? false : true;
    //   }
    // }
    this.heap = this.buildHeap(arr);
    console.log({
      arr,
      heap: this.heap
    });
  }

  buildHeap(arr) {
    let startIdx = Math.floor((arr.length - 1 - 1) / 2);
    while (startIdx >= 0) {
      this.siftDown(arr, startIdx, arr.length - 1);
      startIdx--;
    }
    return arr;
  }

  siftDown(heap, startIdx, endIdx) {
    let currentIndex = startIdx;
    let left = currentIndex * 2 + 1;
    while (left <= endIdx) {
      let min = left;
      let right = currentIndex * 2 + 2;

      if (heap[right] !== undefined && this.comparator(heap[right], heap[left])) {
        min = right;
      }
      
      if (this.comparator(heap[currentIndex], heap[min])) break;

      this.swap(heap, currentIndex, min);
      currentIndex = min;
      left = currentIndex * 2 + 1;
    }
  }

  siftUp(heap, currentIndex) {
    let parentIndex = Math.floor((currentIndex - 1) / 2);
    while (parentIndex >= 0) {
      const isAsc = this.comparator(this.heap[parentIndex], this.heap[currentIndex])
      if (isAsc) break;
      this.swap(heap, parentIndex, currentIndex);
      currentIndex = parentIndex;
      parentIndex =  Math.floor((currentIndex - 1) / 2);
    }
  }

  insert(value) {
    this.heap.push(value);
    this.siftUp(this.heap, this.heap.length - 1);
    return;
  }
  
  remove(value) {
    this.swap(this.heap, 0, this.heap.length - 1);
    const elementToRemove = this.heap.pop();
    this.siftDown(this.heap, 0, this.heap.length - 1);
    return elementToRemove;
  }

  
  peek() {
    return this.heap[0]
  }

  swap(arr, a, b) {
    [arr[b], arr[a]] = [arr[a], arr[b]];
    return arr;
  }

}

// Do not edit the line below.
exports.MinHeap = MinHeap;

// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;
```
