# Permutations -

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-24 at 22.07.42.png" alt=""><figcaption></figcaption></figure>



* bad
* n^n, n\*n!

```jsx
let permutations;
function getPermutations(arr) {
  permutations = [];

  for (const n of arr) {
    permutate(arr, [n]);
  }
  
  return permutations;
}

function permutate(arr, currArr = []) {
  if (arr.length === currArr.length) {
    permutations.push(currArr);
    return;
  }
  
  for (const n of arr) {
    if (currArr.includes(n)) continue;
    permutate(arr, [...currArr, n]);
  }
  
  return;
}

// Do not edit the line below.
exports.getPermutations = getPermutations;
```
