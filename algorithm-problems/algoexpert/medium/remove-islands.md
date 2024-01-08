# Remove Islands -

### **TODO: implement checkLake with iteration**

````jsx
```js
	// can use this
	if (m[i] === undefined) return false; // isThisValid does this
	if (m[i][j] === undefind) return false; // isThisValid does this

	// this is better for safe
	if (i < 0 || i >= m.length) return false;
	if (j < 0 || j >= m[0].length) return fale;
````

````

- m x n, m x n

```jsx
function removeIslands(m) {

  for (let i = 1; i < m.length - 1; i++) {
    for (let j = 1; j < m[0].length - 1; j++) {
      // erase first? and if not a lake revert? X
      // track all 1s and if it forms a lake then erase O
      // do I need visited to check if not visited? X
      // or can I just change 1 to 0? and revert?

      const points = [];
      const isValid = checkLake(m, i, j, points);
      if (isValid) {
        for (const [x, y] of points) {
          m[x][y] = 0;
        }
      }
      
    }
  }

  // revert 2 to 1
  for (let i = 1; i < m.length - 1; i++) {
    for (let j = 1; j < m[0].length - 1; j++) {
      if (m[i][j] !== 2) continue;
      m[i][j] = 1;
    }
  }  
  
  return m;
}

function checkLake(m, i, j, points) {
  // if (m[i] === undefined) return false; // isThisValid does this
  // if (m[i][j] === undefind) return false; // isThisValid does this
  if (m[i][j] !== 1) return true;
  if (isThisValid(m, i, j) === false) return false;
  
  points.push([i, j]);
  m[i][j] = 2;

  const down = checkLake(m, i + 1, j, points);
  const up = checkLake(m, i - 1, j, points);
  const right = checkLake(m, i, j + 1, points);
  const left = checkLake(m, i, j - 1, points);
  
  return down && up && right && left;
}

function isThisValid(m, i, j) {
  if (i === 0 || i === m.length - 1) return false;
  if (j === 0 || j === m[0].length - 1) return false;
  return true;
}

// Do not edit the line below.
exports.removeIslands = removeIslands;
````

