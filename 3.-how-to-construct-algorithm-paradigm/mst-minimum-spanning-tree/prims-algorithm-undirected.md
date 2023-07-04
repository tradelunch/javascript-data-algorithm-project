---
description: Vertex, Priority Queue
---

# Prim's Algorithm: undirected

```jsx
// components count is 2
const edges: number[][] = [
  [
    [1, 3]
  ],
  [
    [0, 3],
    [3, 12]
  ],
  [
    [4, 10],
    [5, 20]
  ],
  [
    [1, 12]
  ],
  [
    [2, 10],
    [5, 15]
  ],
  [
    [2, 20],
    [4, 15]
  ]
];
```

```jsx
// minimum spanning tree Forest
const answer = [
  [
    [1, 3]
  ],
  [
    [0, 3],
    [3, 12]
  ],
  [
    [4, 10]
  ],
  [
    [1, 12]
  ],
  [
    [2, 10],
    [5, 15]
  ],
  [
    [4, 15]
  ]
]
```

### without priority queue

```javascript
// Time: V^2 x V
function prim(edges) {
  if (edges.length < 2) 
    return [];

  const answer = new Array(edges.length);
  // fill weights
  for (let vertex = 0; vertex < edges.length; vertex++) {
    answer[vertex] = new Array();
  }

  const visited = new Array(edges.length).fill(false);
  
  let componentCount = 0;
  // V
  for (let vertex = 0; vertex < edges.length; vertex++) {
    if (visited[vertex] === true) 
      continue;

    // V^2
    findMST(edges, answer, visited, vertex);
    componentCount += 1;
  }

  if (componentCount > 1) {
    console.log('edges forms a minimum spanning FOREEST not TREE');
  }
  
  return answer;
}

function findMinimumIndex(arr) {
  let min = 0;
  
  for (let i = 0; i < arr.length; i++) {
    if (arr[min][0] <= arr[i][0]) continue;
    min = i;
  }
  
  return min;
}

// Time: V^V + (V + E) -> V^2
// Space: V, visited or V + E, answer  
function findMST(edges, answer, visited, start) {

  // E
  const q = [];
  for (const [next, w] of edges[start]) {
    q.push([w, start, next]);
  }
  visited[start] = true;


  // cnt > cnt of vertices V
  let cnt = 1;
  do {

    // V
    // find smallest weight connted from here vertex
    const min = findMinimumIndex(q);
    const lowestWeightedEdge = q[min];

    const [w, here, there] = lowestWeightedEdge;
    q.splice(min, 1);
    
    if(visited[there] === true)
      continue;
    
    answer[here].push([there, w]);
    answer[there].push([here, w]);
    

    // E
    for (const [next, w] of edges[there]) {
      if (visited[next] === true) continue;
      q.push([w, there, next]);
    }
    
    
    // console.log({
    //   visited,
    //   here,
    //   there,
    //   edge: edges[there],
    //   q
    // });

    visited[there] = true;
    
    cnt++;
  } while (q.length !== 0 && cnt < edges.length);
}



// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;
```





### With Priority Queue



change this part

```javascript
    const min = findMinimumIndex(q);
    const lowestWeightedEdge = q[min];
```

to Priority Queue

```javascript
const lowestWeightedEdge = minHeap.remove();
```



> Time: O((V + E)logV) Space: O(V)

why?

* logV?

기본적으로 E가 V보다 갯수가 많다. heap을 구성하는 갯수는 V 갯수가 최대이기 때문에 logV

우리는 기본적으로 V - 1개의 간선이 필요하기 때문이다.

* why? V

모든 V를 돌린다.

* why? E

우리는 각 vertex에 연결된 Edge를 큐에 삽입 한다

모든 간선과 Edge를 방문하고 (V + E) 각각 최소힙 삭제, 삽입을 하기 때문에 (V + E)LogV인데

V ≤ E 이므로 `O(ELogV)`이다

[프림 알고리즘(Prim's Algorithm)](https://8iggy.tistory.com/159)

```jsx
// Time: V^2 x V
function prim(edges) {
  if (edges.length < 2) 
    return [];

  const answer = new Array(edges.length);
  // fill weights
  for (let vertex = 0; vertex < edges.length; vertex++) {
    answer[vertex] = new Array();
  }

  const visited = new Array(edges.length).fill(false);
  
  let componentCount = 0;
  // V
  for (let vertex = 0; vertex < edges.length; vertex++) {
    if (visited[vertex] === true) 
      continue;

    // V^2
    findMSTWithPriorityQueue(edges, answer, visited, vertex);
    componentCount += 1;
  }

  if (componentCount > 1) {
    console.log('edges forms a minimum spanning FOREEST not TREE');
  }
  
  return answer;
}

function findMSTWithPriorityQueue(edges, answer, visited, start) {

  
  // E
  const arr = [];
  for (const [next, w] of edges[start]) {
    arr.push([w, start, next]);
  }

  const predicate = (arr, a, b) => arr[a][0] <= arr[b][0];
  const minHeap = new MinHeap(arr, predicate);
  visited[start] = true;
  console.log('heap:: ', minHeap.heap);

  // cnt > cnt of vertices V
  let cnt = 1;
  while (minHeap.heap.length !== 0 && cnt < edges.length) {
    // V
    const [w, here, there] =  minHeap.remove(); // LogV
    
    if(visited[there] === true)
      continue;
    
    answer[here].push([there, w]);
    answer[there].push([here, w]);

    // E
    for (const [next, w] of edges[there]) {
      if (visited[next] === true) continue;
      minHeap.insert([w, there, next]); // logV
    }

    visited[there] = true;
    cnt++;
  }
}

class MinHeap {
  constructor(arr, predicate = (a, b) => a <= b) {
    this.predicate = predicate;
    this.heap = this.buildHeap(arr);
  }

  buildHeap(arr) {
    let currentIndex = Math.floor((arr.length - 1 - 1) / 2);
    while (currentIndex >= 0) {
      this.siftDown(arr, currentIndex, arr.length - 1);
      currentIndex -= 1;
    }
    console.log('>>> ', arr);
    
    return arr;
  }

  siftDown(heap, currentIndex, endIndex) {
    
    let left = currentIndex * 2 + 1;
    while (left <= endIndex) {
      let min = left;
      const right = currentIndex * 2 + 2;
      if (heap[right] !== undefined && this.predicate(heap, right, min)) {
        min = right;
      }

      if (this.predicate(heap, currentIndex, min)) 
        break;

      this.swap(heap, min, currentIndex);
      currentIndex = min;
      left = currentIndex * 2 + 1;
    }
    
  }

  siftUp(heap, currentIndex) {
    let parentIndex = Math.floor((currentIndex - 1) / 2);
    while (parentIndex >= 0) {
      if (this.predicate(heap, parentIndex, currentIndex)) 
        break;
      this.swap(heap, parentIndex, currentIndex);
      currentIndex = parentIndex;
      parentIndex = Math.floor((currentIndex - 1) / 2);
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

  swap(arr, a, b) {
    const temp = arr[a];
    arr[a] = arr[b];
    arr[b] = temp;
  }
}

// Do not edit the line below.
exports.kruskalsAlgorithm = kruskalsAlgorithm;
```



















