# Selection Sort

> Time: O(N^2) Space: O(1)

```jsx
[8, 5, 2, 9, 5, 6, 3]
```

```jsx
function selectionSort(arr) {

  for (let i = 0; i < arr.length; i++) {
    let minIdx = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[minIdx] <= arr[j]) continue;
      minIdx = j;
    }
    swap(arr, i, minIdx);
  }

  return arr;
}

function swap(arr, a, b) {
  const temp = arr[b];
  arr[b] = arr[a];
  arr[a] = temp;
}

// Do not edit the line below.
exports.selectionSort = selectionSort;
```
