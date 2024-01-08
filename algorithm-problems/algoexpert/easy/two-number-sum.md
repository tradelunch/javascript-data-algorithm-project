# Two Number Sum



<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 14.57.45.png" alt=""><figcaption></figcaption></figure>



```javascript

function twoNumberSum(array, targetSum) {
  const memo = {};

  for (let i = 0; i < array.length; i++) {
    const curr = array[i];
    const diff = targetSum - array[i];

    if (memo[curr] !== undefined) {
      return [memo[curr], curr];
    }
    
    memo[diff] = array[i];
  }
  
  return [];
}

function twoNumberSum(array, targetSum) {
  const memo = {};

  for (let i = 0; i < array.length; i++) {
    const curr = array[i];
    const diff = targetSum - array[i];

    if (memo[curr] !== undefined) {
      return [memo[curr], curr];
    }
    
    memo[diff] = array[i];
  }
  
  return [];
}

// Do not edit the line below.
exports.twoNumberSum = twoNumberSum;
```



```javascript
function twoNumberSum(arr, targetSum) {
  arr.sort((a, b) => a - b);
  
  let s = 0;
  let e = arr.length - 1;
  while (s < e) {
    const start = arr[s];
    const end = arr[e];

    if (start + end === targetSum) {
      return [start, end];
    } else if (start + end > targetSum) {
      e--;
    } else if (start + end < targetSum) {
      s++;
    }
  }

  return [];
}

// Do not edit the line below.
exports.twoNumberSum = twoNumberSum;
```

