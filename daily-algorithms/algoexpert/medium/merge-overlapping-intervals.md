# Merge Overlapping Intervals



* N, 1

```jsx
function mergeOverlappingIntervals(arr) {
  const answer = [];

  arr.sort((a, b) => a[0] - b[0]);

  let range = arr[0];
  for (let i = 1; i < arr.length; i++) {
    const [x1, x2] = range;
    const [y1, y2] = arr[i];

    // -----
    //        ------
    if (x2 < y1) {
      answer.push(range);
      range = arr[i];
      continue;
    }

    // -----
    //  ---
    //     -----
    //   -----
    if (x1 <= y1 && x2 >= y1) {
      range = [x1, Math.max(x2, y2)];
    }
    
  }

  // push last range
  answer.push(range);
  
  return answer;
}

// Do not edit the line below.
exports.mergeOverlappingIntervals = mergeOverlappingIntervals;
```
