# Validate Subsequences



<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 15.00.16 (1).png" alt=""><figcaption></figcaption></figure>

```javascript
function isValidSubsequence(arr, sequence) {
  let idx = 0;
  let seq = 0;
  
  while (seq < sequence.length && idx < arr.length) {
    const curr = sequence[seq];

    if (curr === arr[idx]) {
      seq++;
    }
    
    idx++;
  }

  if (sequence.length !== seq) {
    return false;
  }

  return true;
}

// Do not edit the line below.
exports.isValidSubsequence = isValidSubsequence;
```
