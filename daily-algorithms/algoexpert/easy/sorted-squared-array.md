# Sorted Squared Array

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 15.03.45.png" alt=""><figcaption></figcaption></figure>

```javascript
function sortedSquaredArray(arr) {

  let positiveStart = 0;
  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    if (curr < 0) continue;
    
    positiveStart = i;
    break;
  }

  arr = arr.map(v => v * v);

  const answer = [];
  
  let s = 0;
  let e = arr.length - 1;
  while (s <= e) {
    const start = arr[s];
    const end = arr[e];

    if (start > end) {
      answer.unshift(start);
      s++;
    } else {
      answer.unshift(end);
      e--;
    }

  }

  
  return answer;
}

// Do not edit the line below.
exports.sortedSquaredArray = sortedSquaredArray;
```
