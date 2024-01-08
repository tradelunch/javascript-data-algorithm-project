# Number Of Ways To Traverse Graph

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 22.46.31.png>)

* n x m, n x m
* with matrix

```jsx
function numberOfWaysToTraverseGraph(width, height) {

  const m = new Array(height);
  m[0] = new Array(width).fill(1);
  for (let i = 1; i < height; i++) {
    m[i] = new Array(width).fill(0);
    m[i][0] = 1;
  }
  
  let total = 0;
  for (let i = 1; i < height; i++) {
    for (let j = 1; j < width; ++j) {
      m[i][j] = m[i - 1][j] + m[i][j - 1];
    }
  }
  console.log(m);

  
  return m[height -1][width - 1];
}

// Do not edit the line below.
exports.numberOfWaysToTraverseGraph = numberOfWaysToTraverseGraph;
```

* n + m, 1
* Combination 7 Combination 3

```jsx
// 7! / (3! * 4!)
function numberOfWaysToTraverseGraph(width, height) {

  const numerator = factorial(width - 1 + height - 1);
  const denominator = factorial(width - 1) * factorial(height - 1);
  return Math.floor(numerator / denominator);
}

function factorial(n) {
  let result = 1;

  for (let i = n; i >= 1; --i) {
    result *= i;
  }

  return result;
}

// Do not edit the line below.
exports.numberOfWaysToTraverseGraph = numberOfWaysToTraverseGraph;

```

