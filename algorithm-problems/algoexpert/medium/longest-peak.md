# Longest Peak

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 19.15.09.png>)

* N, 1

```jsx
function longestPeak(arr) {
  arr = [arr[0], ...arr, arr[arr.length - 1]]; // create bumper on before and after this arr

  let max = 0;
  let isPeak = false;
  
  let count = 0;
  for (let i = 1; i < arr.length - 1; i++) {
    const prev = arr[i - 1];
    const curr = arr[i];
    const next = arr[i + 1];

    const isPeak = prev < curr && curr > next;

    if (isPeak === false) continue;

    let leftIdx = i;
    while (leftIdx >= 1 && arr[leftIdx - 1] < arr[leftIdx]) {
      leftIdx--;
    }
    let rightIdx = i;
    while (rightIdx < arr.length - 1 && arr[rightIdx] > arr[rightIdx + 1]) {
      rightIdx++;
    }
    
    const currentPeak = rightIdx - leftIdx + 1;
    max = Math.max(max, currentPeak);
  }

  return max;
}

// Do not edit the line below.
exports.longestPeak = longestPeak;
```
