# Max Subset Sum No Adjacent



![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 22.21.14.png>)

* n, 1

```jsx
function maxSubsetSumNoAdjacent(arr) {

  if (arr.length === 0) return 0;
  if (arr.length === 1) return arr[0];

  let first = arr[0];
  let second = Math.max(arr[1], arr[0]);
  
  for (let i = 2; i < arr.length; i++) {
    const curr = Math.max(second, first + arr[i]);
    first = second;
    second = curr;
  }

  return second;
}

// Do not edit the line below.
exports.maxSubsetSumNoAdjacent = maxSubsetSumNoAdjacent;
```

```jsx
function maxSubsetSumNoAdjacent(arr) {
  if (arr.length === 0) return 0;
  if (arr.length === 1) return arr[0];
  
  let twoStepBefore = arr[0];
  let oneStepBefore = Math.max(arr[0], arr[1]);

  for (let i = 2; i < arr.length; ++i) {
    const curr = arr[i];
    currentSum = twoStepBefore + curr;
    twoStepBefore = oneStepBefore;
    oneStepBefore = Math.max(currentSum, oneStepBefore);
  }
  
  return oneStepBefore;
}

// Do not edit the line below.
exports.maxSubsetSumNoAdjacent = maxSubsetSumNoAdjacent;
```
