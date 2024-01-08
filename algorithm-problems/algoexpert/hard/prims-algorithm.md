# Prim’s Algorithm

![](<../../../.gitbook/assets/Screenshot 2023-11-23 at 22.06.46.png>)

* linear

```jsx
let ans;
let visited;

function primsAlgorithm(edges) {
  ans = [];
  visited = new Array(edges.length).fill(0);

  for (let vertex = 0; vertex < edges.length; vertex++) {
    if (visited[vertex] !== 0) continue;
    findMst(edges, vertex);
  }
  
  return ans;
}

function findMinIdx(arr) {
  let min = Infinity;
  let idx = 0;

  for (let i = 0; i < arr.length; i++) {
    const [w, here, there] = arr[i];
    if (min > w) {
      min = w;
      idx = i;
    }
  }

  return idx;
  
}

function findMst(adjs, vertex) {
  const arr = [];

  const adj = adjs[vertex];
  for (const [there, w] of adj) {
    arr.push([w, vertex, there]);
  }
  visited[vertex] = 1;

  while (arr.length > 0) {
    const  minIdx = findMinIdx(arr);
    const [w, here, there] = arr.splice(minIdx, 1)[0];
    
    if (visited[there] !== 0) continue;

    ans[here] = ans[here] ?? [];
    ans[here].push([there, w]);
    
    ans[there] = ans[there] ?? [];
    ans[there].push([here, w]);

    for (const [next, w] of adjs[there] || []) {
      if (visited[next] !== 0) continue;
      arr.push([w, there, next]);
    }

    visited[there] = 1;
  }
  
}

// Do not edit the line below.
exports.primsAlgorithm = primsAlgorithm;
```

* minHeap

> time: O((E +V) \* log) > O(ElogV) \
> ElogV ⇒ 정점에 연결된 간선에 대해 각각 힙에 넣는 과정 \
> VlogV ⇒ 매 정점마다 최소 간선 찾는 시간

> Space: O(V + E)

```jsx
let ans;
let visited;

function primsAlgorithm(edges) {
  ans = [];
  visited = new Array(edges.length).fill(0);

  for (let vertex = 0; vertex < edges.length; vertex++) {
    if (visited[vertex] !== 0) continue;
    findMst(edges, vertex);
  }
  
  return ans;
}

function findMst(adjs, vertex) {
  const minHeap = new MinHeap([], (a, b) => a[0] < b[0]);

  const adj = adjs[vertex];
  for (const [there, w] of adj) {
    minHeap.insert([w, vertex, there]);
  }
  visited[vertex] = 1;

  while (minHeap.size() > 0) {

    const [w, here, there] = minHeap.remove();
    
    if (visited[there] !== 0) continue;

    ans[here] = ans[here] ?? [];
    ans[here].push([there, w]);
    
    ans[there] = ans[there] ?? [];
    ans[there].push([here, w]);

    for (const [next, w] of adjs[there] || []) {
      if (visited[next] !== 0) continue;
      minHeap.insert([w, there, next]);
    }

    visited[there] = 1;
  }
  
}

class MinHeap {
  constructor(arr = [], predicate = (a, b) => a < b) {
    this.predicate = predicate;
    this.heap = this.buildHeap(arr);
  }

  buildHeap(arr) {
    let currentIdx = Math.floor((arr.length - 1 - 1) / 2);
    while (currentIdx >= 0) {
      this.siftDown(currentIdx, arr.length - 1);
      currentIdx--;
    }
    return arr;
  }

  siftDown(heap, currentIdx, endIdx) {
    let left = currentIdx * 2 + 1;
    
    while (left <= endIdx) {
      const right = currentIdx * 2 + 2;
      let minIdx = left;
      if (heap[right] !== undefined && !this.predicate(heap[left], heap[right])) {
        minIdx = right;
      }

      if (this.predicate(heap[currentIdx], heap[minIdx])) {
        break;
      }

      this.swap(heap, currentIdx, minIdx);
      currentIdx = minIdx;
      left = currentIdx * 2 + 1;
      
    }
    
  }
  
  siftUp(heap, currentIdx) {
    let parentIdx = Math.floor((currentIdx -1) / 2);
    
    while (parentIdx >= 0) {
      if (this.predicate(heap[currentIdx], heap[parentIdx])) {
        this.swap(heap, currentIdx, parentIdx);
        currentIdx = parentIdx;
        parentIdx = Math.floor((currentIdx -1) / 2);
      } else {
        break;
      }
      
    }
    
  }
  insert(v) {
    this.heap.push(v);
    this.siftUp(this.heap, this.heap.length - 1);
  }
  remove() {
    this.swap(this.heap, 0, this.heap.length - 1);
    const elementToRemove = this.heap.pop();
    this.siftDown(this.heap, 0, this.heap.length - 1);
    return elementToRemove;
  }

  size() {
    return this.heap.length;;
  }
  
  swap(arr, a, b) {
    [arr[a], arr[b]] = [arr[b], arr[a]];
    return arr;
  }
}

// Do not edit the line below.
exports.primsAlgorithm = primsAlgorithm;
```



