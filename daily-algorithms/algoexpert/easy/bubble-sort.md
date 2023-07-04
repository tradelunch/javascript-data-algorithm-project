# Bubble Sort

![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 20.26.25.png>)

* average, worst: n^2, 1
* best: n, 1

```jsx
function bubbleSort(arr) {

  let count = 0;
  for (let i = 0; i < arr.length; i++) {
    let count = 0;
    
    for (let j = arr.length - 1; j > i; --j) {
      if (arr[j - 1] <= arr[j]) continue;
      swap(arr, j - 1, j);
      count++;
    }
    
    if (count === 0) return arr;
  }

  return arr;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
  return arr;
}

// Do not edit the line below.
exports.bubbleSort = bubbleSort;
```
