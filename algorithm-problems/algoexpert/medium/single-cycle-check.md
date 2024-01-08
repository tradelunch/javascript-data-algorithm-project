# Single Cycle Check

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 21.05.38.png>)

* n, 1

```jsx
function hasSingleCycle(arr) {

  const visited = new Set();

  let currentIdx = 0;
  while (true) {
    if(visited.has(currentIdx)) {
      break;  
    }
    visited.add(currentIdx);
    currentIdx += arr[currentIdx];
    currentIdx %= arr.length;
    currentIdx += arr.length;
    currentIdx %= arr.length;
  }

  return visited.size === arr.length && currentIdx === 0;
}

// Do not edit the line below.
exports.hasSingleCycle = hasSingleCycle;
```
