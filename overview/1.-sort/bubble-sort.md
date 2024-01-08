# Bubble Sort

> Time: O(N^2) \
> Space: O(1)

```jsx
[8, 5, 2, 9, 5, 6, 3]
```

```jsx
function bubbleSort(arr) {

  let count = 0;
  let idx = 0;
  do {

    count = 0;
    for (let i = arr.length - 1; i >= 1; i--) {
      const prev = arr[i - 1];
      const curr = arr[i];
      if (prev <= curr) continue;

      swap(arr, i - 1, i);
      count++;
    }
    idx++;
  } while (idx < arr.length && count !== 0);

  return arr;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
}

// Do not edit the line below.
exports.bubbleSort = bubbleSort;
```

```jsx
[2, 3, 5, 5, 6, 8, 9]
```
