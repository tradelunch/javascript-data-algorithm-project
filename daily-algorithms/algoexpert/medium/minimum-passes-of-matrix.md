# Minimum Passes Of Matrix

![](<../../../.gitbook/assets/Screenshot 2023-01-24 at 0.11.34.png>)

*

```jsx
let converted = false;
function minimumPassesOfMatrix(m) {
  converted = false;
  
  // let minus = 0;
  let count = 0;
  do {
    const minus = convert(m);
    console.log({ converted, minus, count, m});
    
    if (converted === false) {
      return minus > 0 ? -1 : count;
    }
    
    count++;
  } while (true);

}

// O(m x n), O(n + m)
function convert(m) {
  converted = false;
  
  let minus = 0;
  let points = [];
  for (let i = 0; i < m.length; i++) {
    for (let j = 0; j < m[0].length; j++) {
      const curr = m[i][j];
      if (curr >= 0) continue;
      minus++;
      const flag = canConvertToPositive(m, i, j);
      if (flag === true) points.push([i, j]);
    }
  }

  for (const [x, y] of points) {
    m[x][y] *= -1;
    minus--;
    converted = true;
  }
  
  return minus;
}

function canConvertToPositive(m, i, j) {

  const down = i < m.length - 1 && m[i + 1][j] > 0;
  const up = i > 0 && m[i - 1][j] > 0;
  const right = j < m[0].length - 1 && m[i][j + 1] > 0;
  const left = j > 0 && m[i][j - 1] > 0;
  console.log({
    i,
    j,
    down,
    up,
    right,
    left
  })
  
  return down || up || right || left;
}

// Do not edit the line below.
exports.minimumPassesOfMatrix = minimumPassesOfMatrix;
```
