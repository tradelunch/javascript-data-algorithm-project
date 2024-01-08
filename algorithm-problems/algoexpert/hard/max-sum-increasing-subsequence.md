# Max Sum Increasing Subsequence

![](<../../../.gitbook/assets/Screenshot 2023-02-18 at 14.35.20.png>)

* n^2, n

```jsx
function maxSumIncreasingSubsequence(arr) {

  const sums = arr.map((v, idx) => [idx, v]);

  for (let i = 1; i < arr.length; i++) {
    const curr = arr[i];
    for (let j = i - 1; j >= 0; j--) {
      const prev = arr[j];
      if (prev >= curr) continue;
      if (sums[i][1] > sums[j][1] + curr) continue;
      const check = Math.max(sums[i][1], sums[j][1] + curr)
      sums[i] = [j, check];
    }
    
  }
  
  let max = -Infinity;
  let maxIdx = 0;
  for (let i = 0; i < arr.length; i++) {
    const [idx, sum] = sums[i];
    if (max < sum) {
      max = sum;
      maxIdx = i;
    }
  }

  const seqs = [];
  let currentIdx = maxIdx;
  while (currentIdx !== sums[currentIdx][0]) {
    seqs.push(arr[currentIdx]);
    const [idx, sum] = sums[currentIdx];
    currentIdx = sums[currentIdx][0];
  }

  return [max, seqs.reverse()];
  
}

// Do not edit the line below.
exports.maxSumIncreasingSubsequence = maxSumIncreasingSubsequence;
```
