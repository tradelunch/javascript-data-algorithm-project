# Product Sum

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 19.55.24 (1).png" alt=""><figcaption></figcaption></figure>

```jsx
// Tip: You can use the Array.isArray function to check whether an item
// is a list or an integer.
function productSum(arr) {
  return findProductSum(arr);
}

function findProductSum(arr, depth = 1) {

  let sum = 0;
  for (const value of arr) {
    if (!Array.isArray(value)) {
      sum += value;
      continue;
    }

    sum += findProductSum(value, depth + 1);
  }

  return sum * depth;

  
}

// Do not edit the line below.
exports.productSum = productSum;
```
