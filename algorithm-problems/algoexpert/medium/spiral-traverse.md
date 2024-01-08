# Spiral Traverse

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 16.41.58.png>)

* NxM, 1

```jsx
function spiralTraverse(arr) {
  const answer = [];
  

  let startCol = 0;
  let endCol = arr[0].length - 1;

  let startRow = 0;
  let endRow = arr.length - 1;
  while (endCol - startCol >= 0 && endRow - startRow >= 0) {

    // right
    for (let col = startCol; col <= endCol; col++) {
      answer.push(arr[startRow][col]);
    }

    // down
    startRow++;
    for (let row = startRow; row <= endRow; row++) {
      answer.push(arr[row][endCol]);
    }

    // left
    endCol--;
    for (let col = endCol; col >= startCol; col--) {
      if (startRow > endRow) break;
      answer.push(arr[endRow][col]);
    }

    // up
    endRow--;
    for (let row = endRow; row >= startRow; row--) {
      if (startCol > endCol) break;
      answer.push(arr[row][startCol]);
    }

    startCol++;

  }

  return answer;
}

// Do not edit the line below.
exports.spiralTraverse = spiralTraverse;
```
