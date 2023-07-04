# Binary Search



<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 20.00.11.png" alt=""><figcaption></figcaption></figure>

### Binary Search has to be sorted before running

```jsx
function binarySearch(arr, target) {

  arr.sort((a, b) => a - b); // sorted Time complexity of insertion sort => n
  
  let s = -1;
  let e = arr.length;
  while (s + 1 < e) {
    const m = s + Math.floor((e - s) / 2);

    if (arr[m] >= target) {
      e = m;
    } else {
      s = m
    }
    
  }

  if (arr[e] !== target) 
    return -1;

  return e;
}

// Do not edit the line below.
exports.binarySearch = binarySearch;
```

