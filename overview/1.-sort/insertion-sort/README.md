# Insertion Sort

> Time: O(N^2) → O(N) best when sorted already

> Space: O(1)

```jsx
[8, 5, 2, 9, 5, 6, 3]
```

```jsx
function insertionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    for (let j = i - 1; j >= 0; j--) {
      if (arr[j] <= curr) break;
      swap(arr, j, j + 1);
    }
  }

  return arr;
}

function swap(arr, a, b) {
  const temp = arr[a];
  arr[a] = arr[b];
  arr[b] = temp;
}

// Do not edit the line below.
exports.insertionSort = insertionSort;
```
