# First Duplicate Number

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 20.45.41.png>)

* N, N

```jsx
function firstDuplicateValue(arr) {
  const memo = new Set();

  for (let i = 0; i < arr.length; i++) {
    const num = arr[i];
    if (memo.has(num)) return arr[i];
    memo.add(num);
  }
  
  return -1;
}

// Do not edit the line below.
exports.firstDuplicateValue = firstDuplicateValue;
```

* N, 1

```jsx
function firstDuplicateValue(arr) {

  for (let i = 0; i < arr.length; i++) {
    const num = Math.abs(arr[i]);
    if (arr[num - 1] < 0) return num;
    arr[num - 1] = arr[num - 1] * -1;
  }
  
  return -1;
}

// Do not edit the line below.
exports.firstDuplicateValue = firstDuplicateValue;
```
