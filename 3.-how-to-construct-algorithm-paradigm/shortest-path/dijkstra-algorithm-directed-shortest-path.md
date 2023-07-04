# Dijkstra algorithm: directed, shortest path

<mark style="color:blue;">다익스트라 알고리즘은 간선에 가중치가 있는 방향 그래프에서 최단거리 경로를 구하기 위해 사용한다</mark>. 따라서 만약 방향 그래프가 아니라면 하나의 간선에 대해 양방향으로 이어지는 방향 그래프로 변환해야 한다. 즉, 무방향 그래프로 데이터가 주어지는 경우 그래프를 인접 리스트 형태로 만들어줄 필요가 있다.

## Dijkstra



[prim-vs-dijkstra.md](../greedy-algorithm/prim-vs-dijkstra.md "mention")



{% embed url="https://nearhome.tistory.com/138" %}

![](<../../.gitbook/assets/Screenshot 2023-06-15 at 23.30.49.png>)





> Time: O(v^2 + e)

> Space: O(V)

> with out heap

```jsx
function Node(v, predecessor, cost) {
  this.v = v;
  this.predecessor = predecessor;
  this.cost = cost;
}

function findMinimumCostVertex(nodes, visited) {
  let currentMinConst = Infinity;
  let here = -1;

  for (let vertex = 0; vertex < nodes.length; vertex++) {
    if (visited.has(vertex)) continue;

    const cost = nodes[vertex].cost;
    if (cost < currentMinConst) {
      currentMinConst = cost;
      here = vertex;
    }
  }

  return [here, currentMinConst];
}

function dijkstrasAlgorithm(start, edges) {

  const nodes = [];
  // initialize
  for (let i = 0; i < edges.length; i++) {
    const node = new Node(i, i, Infinity);
    nodes[i] = node;
  }

  nodes[start].cost = 0;
  const visited = new Set();

  while (visited.size !== edges.length) {
    const [here, currentMinCost] = findMinimumCostVertex(nodes, visited);
    // console.log(here, currentMinCost);

    // visited a vertex with Infinity > can not reach there
    if (currentMinCost === Infinity) {
      break;
    }
    
    const adj = edges[here] ?? [];
    for (const [there, cost] of adj) {
      if (visited.has(there)) continue;
      
      const prev = nodes[there].cost; // current min there cost
      const next = currentMinCost + cost;
      if (prev > next) {
        nodes[there].predecessor = here;
        nodes[there].cost = next;
      }
    }

    visited.add(here);

    // break;
  }

  const answer = [];
  for (let i = 0; i < edges.length; i++) {
     if (nodes[i].cost === Infinity) {
        answer[i] = -1;
     } else {
        answer[i] = nodes[i].cost;
     }

    console.log(nodes[i]);
  }

  return answer;
  
}

// Do not edit the line below.
exports.dijkstrasAlgorithm = dijkstrasAlgorithm;
```

## With Priority Queue

### With visited Array

> Time: O((v + e)logv ⇒ elogV)

> Space: O(v)

> using visited array not to add visited vertex

```jsx
function Node(vertex, predecessor, cost) {
  this.vertex = vertex;
  this.predecessor = predecessor;
  this.cost = cost;
}

// O((V + E)logV => ElogV, usually E > V)
function dijkstrasAlgorithm(start, edges) {

  const dist = [];
  for (let vertex = 0; vertex < edges.length; vertex++) {
    dist[vertex] = new Node(vertex, vertex, Infinity);
  }
  
  const visited = new Set();
  dist[start].cost = 0;
  const minHeap = new Heap([], (a, b) => a.cost <= b.cost);
  minHeap.insert(new Node(start, start, 0));

  while (minHeap.size > 0) {
    const {
      vertex: here,
      predecessor,
      cost: currentCost,
    } = minHeap.remove();

    const adj = edges[here];
    for (const [there, incommingCost] of adj) {
      if (visited.has(there)) continue;
      
      const prev = dist[there].cost;
      const next = currentCost + incommingCost;
      if (prev > next) {
        dist[there].cost = next;
        dist[there].predecessor = here;
        
        minHeap.insert(new Node(there, here, next));
      }
    }

    console.log(minHeap.heap);

    visited.add(here);
  }
  const answer = [];
  for (let vertex = 0; vertex < edges.length; vertex++) {
    const node = dist[vertex];
    answer[vertex] = node.cost === Infinity ? -1 : node.cost;
  }

  return answer;
}

class Heap {
    constructor(arr, predicate = (a, b) => a <= b) {
        this.predicate = predicate;
        this.size = arr.length;
        this.heap = this.buildHeap(arr);
    }

    buildHeap(arr) {
        let currentIndex = Math.floor((arr.length - 1 - 1) / 2);
        while (currentIndex >= 0) {
            this.siftDown(arr, currentIndex, arr.length - 1);
            currentIndex--;
        }

        return arr;
    }

    insert(v) {
        this.heap.push(v);
        this.size++;

        this.siftDown(this.heap, 0, this.heap.length - 1);

    }

    remove(v) {
        this.swap(this.heap, 0, this.heap.length - 1);
        const elementToRemove = this.heap.pop();
        this.size--;
        
        this.siftDown(this.heap, 0, this.heap.length - 1);
        return elementToRemove;
    }

    siftUp(heap, currentIndex) {
        let parentIndex = Math.floor((currentIndex - 1) / 2);
        while (parentIndex >= 0) {
            if (this.predicate(heap[parentIndex], heap[currentIndex])) {
                break;
            }

            this.swap(heap, parentIndex, currentIndex);
            currentIndex = parentIndex;
            parentIndex = Math.floor((currentIndex - 1) / 2);
        }
        return heap;
    }

    siftDown(heap, currentIndex, endIndex) {
        let left = currentIndex * 2 + 1;

        while (left <= endIndex) {
            let min = left;
            const right = currentIndex * 2 + 2;
            if (heap[right] !== undefined && this.predicate(heap[right], heap[min])) {
                min = right;
            }

            if (this.predicate(heap[currentIndex], heap[min])) break;
            this.swap(heap, currentIndex, min);
            currentIndex = min;
            left = currentIndex * 2 + 1;
        }

        return heap;
    }

    swap(arr, a, b) {
        [arr[b], arr[a]] = [arr[a], arr[b]];
    }

}

// Do not edit the line below.
exports.dijkstrasAlgorithm = dijkstrasAlgorithm;
```

### without visited Array

```jsx
function Node(vertex, predecessor, cost) {
  this.vertex = vertex;
  this.predecessor = predecessor;
  this.cost = cost;
}

// O((V + E)logV => ElogV, usually E > V)
function dijkstrasAlgorithm(start, edges) {

  const dist = [];
  for (let vertex = 0; vertex < edges.length; vertex++) {
    dist[vertex] = new Node(vertex, vertex, Infinity);
  }
  
  const minHeap = new Heap([], (a, b) => a.cost <= b.cost);
  dist[start].cost = 0;
  minHeap.insert(new Node(start, start, 0));

  while (minHeap.size > 0) {
    const {
      vertex: here,
      predecessor,
      cost: currentCost,
    } = minHeap.remove();

    // we pu every connected nodes into heap
    // so we filter smallest cost from heap is bigger than or equal to current distance min
    // without using visited array
    if (dist[here].cost < currentCost) 
      continue;

    const adj = edges[here];
    for (const [there, incommingCost] of adj) {
      
      const prev = dist[there].cost;
      const next = currentCost + incommingCost;
      if (prev > next) {
        dist[there].cost = next;
        dist[there].predecessor = here;
        
        minHeap.insert(new Node(there, here, next));
      }
    }

    console.log(minHeap.heap);
  }
  
  const answer = [];
  for (let vertex = 0; vertex < edges.length; vertex++) {
    const node = dist[vertex];
    answer[vertex] = node.cost === Infinity ? -1 : node.cost;
  }

  return answer;
}

class Heap {
    constructor(arr, predicate = (a, b) => a <= b) {
        this.predicate = predicate;
        this.size = arr.length;
        this.heap = this.buildHeap(arr);
    }

    buildHeap(arr) {
        let currentIndex = Math.floor((arr.length - 1 - 1) / 2);
        while (currentIndex >= 0) {
            this.siftDown(arr, currentIndex, arr.length - 1);
            currentIndex--;
        }

        return arr;
    }

    insert(v) {
        this.heap.push(v);
        this.size++;

        this.siftDown(this.heap, 0, this.heap.length - 1);

    }

    remove(v) {
        this.swap(this.heap, 0, this.heap.length - 1);
        const elementToRemove = this.heap.pop();
        this.size--;
        
        this.siftDown(this.heap, 0, this.heap.length - 1);
        return elementToRemove;
    }

    siftUp(heap, currentIndex) {
        let parentIndex = Math.floor((currentIndex - 1) / 2);
        while (parentIndex >= 0) {
            if (this.predicate(heap[parentIndex], heap[currentIndex])) {
                break;
            }

            this.swap(heap, parentIndex, currentIndex);
            currentIndex = parentIndex;
            parentIndex = Math.floor((currentIndex - 1) / 2);
        }
        return heap;
    }

    siftDown(heap, currentIndex, endIndex) {
        let left = currentIndex * 2 + 1;

        while (left <= endIndex) {
            let min = left;
            const right = currentIndex * 2 + 2;
            if (heap[right] !== undefined && this.predicate(heap[right], heap[min])) {
                min = right;
            }

            if (this.predicate(heap[currentIndex], heap[min])) break;
            this.swap(heap, currentIndex, min);
            currentIndex = min;
            left = currentIndex * 2 + 1;
        }

        return heap;
    }

    swap(arr, a, b) {
        [arr[b], arr[a]] = [arr[a], arr[b]];
    }

}

// Do not edit the line below.
exports.dijkstrasAlgorithm = dijkstrasAlgorithm;
```
