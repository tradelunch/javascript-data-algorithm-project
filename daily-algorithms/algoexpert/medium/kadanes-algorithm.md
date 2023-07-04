# Kadane’s Algorithm

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 18.46.53.png>)

* first try

```jsx
function kadanesAlgorithm(arr) {
  let max = arr[0];
  let sum = arr[0];

  for (let i = 1; i < arr.length; i++) {
    const curr = arr[i];
    const currentSum = sum + curr;
    max = Math.max(currentSum, max, curr);
    sum = Math.max(currentSum, 0);
  }

  return max;
}

// Do not edit the line below.
exports.kadanesAlgorithm = kadanesAlgorithm;
```

* second try
* remove currenSum

```jsx
function kadanesAlgorithm(arr) {
  let max = arr[0];
  let sum = arr[0];

  for (let i = 1; i < arr.length; i++) {
    const curr = arr[i];
    // from this line, if sum < 0, sum = curr
    // basically filter sum less than 0
    sum = Math.max(sum + curr, curr); 
    max = Math.max(sum, max);
  }

  return max;
}

// Do not edit the line below.
exports.kadanesAlgorithm = kadanesAlgorithm;
```
