# River Sizes -

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-23 at 21.24.34.png" alt=""><figcaption></figcaption></figure>

* m x n, m x n

```jsx
let visited;

function riverSizes(matrix) {
  const answer = [];
  
  visited = new Array(matrix.length);
  for (let i = 0; i < matrix.length; i++){
    visited[i] = new Array(matrix[0].length).fill(0); 
  }

  for (let i = 0; i < matrix.length; i++) {
    for (let j = 0; j < matrix[0].length; j++) {
      if (matrix[i][j] === 0) continue;
      
      if (visited[i][j] === 1) continue;
      // visited[i][j] = 1;
      const memo = { count: 0 };
      searchLake(matrix, i, j, visited, memo);
      answer.push(memo.count);
    }
  }

  return answer;
}

function searchLake(matrix, i, j, visited, memo) {
  if (visited[i][j] === 1) return memo;
  if (matrix[i][j] !== 1) return memo;
  memo.count += 1;
  visited[i][j] = 1;
  
  if (i < matrix.length - 1) {
    searchLake(matrix, i + 1, j, visited, memo);
  }
  if (j < matrix[0].length - 1) {
    searchLake(matrix, i, j + 1, visited, memo);
  }
  if (i > 0) {
    searchLake(matrix, i - 1, j, visited, memo);
  }
  if (j > 0) {
    searchLake(matrix, i, j - 1, visited, memo);
  }

  return memo;
}

// Do not edit the line below.
exports.riverSizes = riverSizes;
```
