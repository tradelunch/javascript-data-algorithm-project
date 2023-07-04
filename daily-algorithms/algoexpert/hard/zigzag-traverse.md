# Zigzag Traverse

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 14.12.50.png>)

* n, 1

```jsx
function zigzagTraverse(matrix) {
  const answer = [matrix[0][0]];
  const rowLen = matrix.length;
  const colLen = matrix[0].length;

  let row = 0;
  let col = 0;

  while (true) {
    if (row === rowLen - 1 && col === colLen - 1) break;

    // going right
    if (row === rowLen - 1 && col < colLen - 1) {
      col += 1;
    }
    // going down
    if(col === 0 && row < rowLen - 1) {
      row += 1;
    }

    while (row >= 0 && col < colLen) {
      answer.push(matrix[row][col]);
      row--;
      col++;
    }
    row++;
    col--;

    if (row === rowLen - 1 && col === colLen - 1) break;

    // going down
    if (col === colLen - 1 && row < rowLen - 1) {
      row += 1;
    }

    // going right
    if (row === 0 && col < colLen - 1) {
      col += 1;
    }    

    while (col >= 0 && row < rowLen) {
      answer.push(matrix[row][col]);
      row++;
      col--;
    }
    row--;
    col++;

    if (row === rowLen - 1 && col === colLen - 1) break;
  }
  
  return answer;
}

// Do not edit the line below.
exports.zigzagTraverse = zigzagTraverse;
```

* another way
* n, n

```jsx
function zigzagTraverse(matrix) {
  const answer = [];
  const height = matrix.length;
  const width = matrix[0].length;

  let row = 0;
  let col = 0;
  let movingDownward = true;
  while (!isOutOfBounds(row, col, height, width)) {
    answer.push(matrix[row][col]);
    if (movingDownward) {
      if (col === 0 || row === height - 1) {
        movingDownward = false;
        if (row === height - 1) {
          col++;
        } else if (col === 0) {
          row++;
        }
      } else {
        row++;
        col--;
      }
      continue;
    }

    if (col === width - 1 || row === 0) {
      movingDownward = true;
      if (col === width - 1) {
        row++;
      } else if (row === 0) {
        col++;
      }
    } else {
      row--;
      col++;
    }

  }

  return answer;
}

function isOutOfBounds(row, col, height, width) {
  return row < 0 || col < 0 || row > height - 1 || col > width - 1;
}

// Do not edit the line below.
exports.zigzagTraverse = zigzagTraverse;
```
