# Merge Sort

![](<../../../.gitbook/assets/Screenshot 2023-04-15 at 16.54.41.png>)

* nlogn, n

```jsx
function mergeSort(arr) {
  return mergeSortHelper(arr, 0, arr.length - 1);
}

function mergeSortHelper(arr, s, e) {
  if (s >= e) {
    return [arr[s]];
  }
  
  const m = s + Math.floor((e - s) / 2);

  const arr1 = mergeSortHelper(arr, s, m);
  const arr2 = mergeSortHelper(arr, m + 1, e);

  return merge(arr1, arr2);
}

function merge(arr1, arr2) {
  const merged = new Array(arr1.length + arr2.length);
  let currIdx = 0;
  
  let idx1 = 0;
  let idx2 = 0;
  while (idx1 < arr1.length && idx2 < arr2.length) {
    const v1 = arr1[idx1];
    const v2 = arr2[idx2];

    if (v1 <= v2) {
      merged[currIdx] = v1;
      idx1++;
    } else {
      merged[currIdx] = v2;
      idx2++;
    }

    currIdx++;
  }

  while (idx1 < arr1.length) {
    merged[currIdx] = arr1[idx1];
    idx1++;
    currIdx++;
  }

  while (idx2 < arr2.length) {
    merged[currIdx] = arr2[idx2];
    idx2++;
    currIdx++;
  }

  return merged;
}

// Do not edit the line below.
exports.mergeSort = mergeSort;
```
