# Zero Sum Subarray + find indices of sub array

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 21.15.30.png>)

* N, N

```jsx
function zeroSumSubarray(nums) {

  let set = new Set([0]);
  
  let currentSum = 0;
  for (let i = 0; i < nums.length; i++) {
    currentSum += nums[i];
    if (set.has(currentSum)) return true;
    set.add(currentSum);
  }
  
  return false;
}

// Do not edit the line below.
exports.zeroSumSubarray = zeroSumSubarray;
```

* Can I find index?

```jsx
function zeroSumSubarray(nums) {

  const answer = [];
  let set = new Set([0]);
  let sums = [];

  let idxToStop = -1;
  let currentSum = 0;
  for (let i = 0; i < nums.length; i++) {
    currentSum += nums[i];
    sums[i] = currentSum;
    if (set.has(currentSum)) {
      idxToStop = i;
      answer.push(idxToStop);
      break;
    }
    set.add(currentSum);
  }

  if (idxToStop === -1) return [];

  for (let i = idxToStop - 1; i >= 0; --i) {
    if (sums[i] === currentSum) break;
    answer.push(i);
  }
  
  
  return answer;
}

// Do not edit the line below.
exports.zeroSumSubarray = zeroSumSubarray;
```
