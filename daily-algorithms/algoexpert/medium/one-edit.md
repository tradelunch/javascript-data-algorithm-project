# One Edit

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 17.32.02.png>)

* n, 1

```tsx
function oneEdit(stringOne, stringTwo) {
  const len1 = stringOne.length;
  const len2 = stringTwo.length;
  
  if (Math.abs(len1 - len2) > 1) return false; 
  
  let idx1 = 0;
  let idx2 = 0;
  let count = 0;
  while (idx1 < len1 && idx2 < len2) {
    if (stringOne[idx1] === stringTwo[idx2]) {
      idx1++;
      idx2++;
      continue;
    }
    if (count > 0) return false;
    count++;

    if (len1 === len2) {
      idx1++;
      idx2++;
    } else if (len1 > len2) {
      idx1++;
    } else if (len1 < len2) {
      idx2++;
    }
    
  }

  return true;
}

// Do not edit the line below.
exports.oneEdit = oneEdit;
```
