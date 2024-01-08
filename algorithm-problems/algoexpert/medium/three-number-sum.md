# Three Number Sum



![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 21.58.58.png>)

* brute force
* n^3, 1

```jsx
function threeNumberSum(arr, targetSum) {
  arr.sort((a, b) => a - b);
  const answer = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      for (let k = j + 1; k < arr.length; k++) {
        if (arr[i] + arr[j] + arr[k] === targetSum) 
          answer.push([arr[i], arr[j], arr[k]]);
      }
    }
  }
  return answer;
}

// Do not edit the line below.
exports.threeNumberSum = threeNumberSum;
```

* memo
* n^2, n

```jsx
function threeNumberSum(arr, targetSum) {
  arr.sort((a, b) => a - b);

  const memo = {}
  for (let i = 0; i < arr.length; i++) {
    const diff = targetSum - arr[i];
    memo[diff] = [arr[i], i];
  }
  
  const answer = [];
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      const diff = arr[i] + arr[j];
      if (memo[diff] === undefined) continue;
      if (memo[diff][1] <= j) continue;
      answer.push([arr[i], arr[j], memo[diff][0]]);
    }
  }
  return answer;
}

// Do not edit the line below.
exports.threeNumberSum = threeNumberSum;
```

* two pointer
* n^2, 1 (except answer)

```jsx
function threeNumberSum(arr, targetSum) {
  arr.sort((a, b) => a - b);
  
  const answer = [];
  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    
    let s = i + 1;
    let e = arr.length - 1;
    while(s < e) {
      const currentSum = curr + arr[s] + arr[e];
      if (currentSum === targetSum) {
        answer.push([curr, arr[s], arr[e]]);
        e--;
        s++;
      } else if (currentSum > targetSum) {
        e--;
      } else if (currentSum < targetSum) {
        s++;
      }
    }
  }
  
  return answer;
}

// Do not edit the line below.
exports.threeNumberSum = threeNumberSum;
```
