# Find Three Largest Sum

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 20.15.23.png" alt=""><figcaption></figcaption></figure>



* n, 1
* creating new array

```jsx
function findThreeLargestNumbers(arr) {
  let largest = [-Infinity, -Infinity, -Infinity];

  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    if (curr < largest[0]) continue;

    const temp = [];
    for (let j = 2; j >=0; --j){
      const large = largest[j];
      if (curr <= large)
        continue;
      largest = [...largest.slice(1, j + 1), curr, ...largest.slice(j + 1)];
      break;
    }
  }

  return largest; 
}

// Do not edit the line below.
exports.findThreeLargestNumbers = findThreeLargestNumbers;
```

* swap

```jsx
function findThreeLargestNumbers(arr) {
  const largest = [-Infinity, -Infinity, -Infinity];

  for (const n of arr) {
    let curr = n;
    for (let i = 2; i >= 0; --i) {
      const large = largest[i];
      if (large >= curr) continue;
      largest[i] = curr;
      curr = large;
    }
  }

  return largest; 
}

// Do not edit the line below.
exports.findThreeLargestNumbers = findThreeLargestNumbers;
```
