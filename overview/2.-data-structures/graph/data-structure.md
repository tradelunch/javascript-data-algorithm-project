---
description: How to store Graph data in a code?
---

# Data Structure

## Graph To Use

### Directed Graph



### Undirected Graph



### Max number of Edges

```javascript
// undirected
n(n - 1) / 2

// directed graph
n(n - 1)
```



## Adjacent List

### Directed Graph

![](<../../../.gitbook/assets/Screenshot 2023-06-05 at 13.26.00.png>)

<pre class="language-javascript"><code class="lang-javascript"><strong>const adjs = [
</strong>    [1],
    [2, 3],
    [3],
    [0]
];
</code></pre>

### Undirected Graph

above example

```javascript
const adjs = [
    [1, 3],
    [0, 2, 3],
    [1, 3],
    [0, 1, 2]
];
```

<figure><img src="../../../.gitbook/assets/Screenshot 2023-06-05 at 13.26.22.png" alt=""><figcaption></figcaption></figure>

```javascript
const adjs = [
    [1, 4],
    [0, 3, 4, 2],
    [1, 3],
    [1, 2, 4],
    [0, 1, 3]
];
```



reference

* [https://www.geeksforgeeks.org/print-adjacency-list-for-a-directed-graph/](https://www.geeksforgeeks.org/print-adjacency-list-for-a-directed-graph/)
* [https://www.geeksforgeeks.org/graph-and-its-representations/](https://www.geeksforgeeks.org/graph-and-its-representations/)



## Matrix



