# Selection Sort



* always: n^2, 1

```jsx
function selectionSort(arr) {

  for (let i = 0; i < arr.length; i++) {
    let smallest = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[smallest] <= arr[j]) continue;
      smallest = j;
    }

    swap(arr, i, smallest);
  }
  
  return arr;
}

function swap(arr, a, b) {
  // const temp = arr[a];
  // arr[a] = arr[b];
  // arr[b] = temp;

  [arr[b], arr[a]] = [arr[a], arr[b]];

  return arr;
}

// Do not edit the line below.
exports.selectionSort = selectionSort;
```
