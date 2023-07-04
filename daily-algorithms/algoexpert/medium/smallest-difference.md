# Smallest Difference

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 15.14.58.png>)

*

```jsx
function smallestDifference(arrayOne, arrayTwo) {
  arrayOne.sort((a, b) => a - b);
  arrayTwo.sort((a, b) => a - b);
  
  let min = Math.abs(arrayOne[0] - arrayTwo[0]);
  let tuple = [arrayOne[0], arrayTwo[0]];

  let idx1 = 0;
  let idx2 = 0;
  let diff = min;
  while (idx1 < arrayOne.length && idx2 < arrayTwo.length) {
    const diff = Math.abs(arrayOne[idx1] - arrayTwo[idx2]);
    
    if (diff < min) {
      min = diff;
      tuple = [arrayOne[idx1], arrayTwo[idx2]];
    }

    if (diff === 0) {
      return [arrayOne[idx1], arrayTwo[idx2]];
    } else if (arrayOne[idx1] < arrayTwo[idx2]) {
      idx1++;
    } else if (arrayOne[idx1] > arrayTwo[idx2]) {
      idx2++;
    }
  }

  return tuple;

}

// Do not edit the line below.
exports.smallestDifference = smallestDifference;
```
