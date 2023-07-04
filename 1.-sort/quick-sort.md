# Quick Sort



> Time: O(nlogn)

> Space: O(n)

```jsx
function quickSort(arr) {
  quickSortHelper(arr, 0, arr.length - 1);
  return arr;
}

function partition(arr, s, e) {
  let pointer = s;
  let left = s;
  while (left < e) {
    if (arr[left] < arr[e]) {
      swap(arr, left, pointer);
      pointer++;
    }  

    left++;
  }

  swap(arr, pointer, e);
  return pointer;
}

function quickSortHelper(arr, s, e) {
  if (s >= e) {
    return;
  }
  
  const pivotIndex = partition(arr, s, e);
  const left = quickSortHelper(arr, s, pivotIndex - 1);
  const right = quickSortHelper(arr, pivotIndex + 1, e);
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
}

// Do not edit the line below.
exports.quickSort = quickSort;
```

```jsx
function quickSort(arr) {

  quickSortHelper(arr, 0, Math.max(arr.length - 1, 0));
  
  return arr;
}

function quickSortHelper(arr, start, end) {
    if (start >= end) {
        return;
    }

    let left = start;
    let right = end - 1;

    let pivot = end;

    while (left <= right) {
      // const low = arr[left]; // 이렇게 사용하면 안 된다   
      // const high = arr[right]; // swap 하면 원하는 결과를 얻기 힘들다

      if (arr[right] <= arr[pivot] && arr[left] > arr[pivot]) {
        swap(arr, left, right);      
      }
      
      if (arr[right] >= arr[pivot]) {
          right--;
      }

      if (arr[left] <= arr[pivot]) {
          left++;
      }
    }

    console.log('result', {
        start,
        end,
        arr,
        left,
        right,
        pivot,
    });
    swap(arr, pivot, left);
    pivot = left;
  
    quickSortHelper(arr, start, pivot - 1);
    quickSortHelper(arr, pivot + 1, end);
}

function swap(arr, a, b) {
  [arr[a], arr[b]] = [arr[b], arr[a]];
  return arr;
}

// Do not edit the line below.
exports.quickSort = quickSort;

function quickSort(arr) {

  quickSortWidthEndPivot(arr, 0, arr.length - 1);
  return arr;
}

function quickSortWidthEndPivot(arr, start, end) {
    if (start >= end) {
        return arr;
    }

    let left = start;
    let right = end - 1;
    let pivot = end;

   
    while (left <= right) {
      const low = arr[left];
      const high = arr[right];

      if (low > arr[pivot] && high < arr[pivot]) {
        swap(arr, left, right);  
      }

      if (arr[left] <= arr[pivot]) {
        left++;
      }
      if (arr[right] >= arr[pivot]) {
        right--;
      }

      console.log({
        start, end, pivot,
        left,
        right,
        arr
      });
    }
    console.log('>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>');
    swap(arr, left, pivot);
    pivot = left;

    quickSortWidthEndPivot(arr, start, pivot - 1);
    quickSortWidthEndPivot(arr, pivot + 1, end);

    return arr;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
}

// Do not edit the line below.
exports.quickSort = quickSort;
```
