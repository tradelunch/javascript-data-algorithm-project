# Four Number Sum

![](<../../../.gitbook/assets/Screenshot 2023-02-10 at 21.35.42.png>)

* n^3, n

```jsx
function fourNumberSum(arr, targetSum) {

  const memo = {};

  const answer = [];
  for (let i = 0; i < arr.length; i++) {
    const diff = targetSum - arr[i];
    memo[diff] = [i, arr[i]];
  }
  
  for (let i = 0; i < arr.length; i++) {
    for (let j = i + 1; j < arr.length; j++) {
      for (let k = j + 1; k < arr.length; k++) {
        const sumThree = arr[i] + arr[j] + arr[k];
        if (memo[sumThree] === undefined) continue;
        
        const [idx, value] = memo[sumThree];
        if (k >= idx) continue;
        answer.push([arr[i], arr[j], arr[k], value]);
      }
    }
  }

  return answer;
}

exports.fourNumberSum = fourNumberSum;
```

* n^2 ⇒ n^3, n^2
*

```jsx
function fourNumberSum(arr, targetSum) {

  const memo = {};
  const answer = [];

  for (let i = 1; i < arr.length; i++) {
    
    for (let j = i + 1; j < arr.length; j++) {
      const currentSum = arr[i] + arr[j];
      const diff = targetSum - currentSum;
      console.log(memo);
      console.log({ diff });
      
      if (memo[diff] === undefined) continue;
      
      for (const pair of memo[diff]) {
        const p = [arr[i], arr[j], ...pair];
        answer.push(p);
      }

    }

    const second = arr[i];
    for (let k = 0; k < i; k++) {
      const first = arr[k];
      if (memo[first + second] === undefined) memo[first + second] = [];
      memo[first + second].push([first, second]);
    }

  }
  
  return answer;
}

// Do not edit the line below.
exports.fourNumberSum = fourNumberSum;
```
