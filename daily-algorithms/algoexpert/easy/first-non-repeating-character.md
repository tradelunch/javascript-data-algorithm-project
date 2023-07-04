# First Non Repeating Character

![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 21.16.11.png>)

* n, 1 (alphabet 26 constant)

```jsx
function firstNonRepeatingCharacter(str) {
  const memo = {}
  for (let i = 0; i < str.length; i++) {
    const c = str[i];
    if (memo[c] === undefined) memo[c] = 0;
    memo[c] += 1;
  }

  for (let i = 0; i < str.length; i++) {
    const c = str[i];
    if (memo[c] === 1) return i;
  }
  
  return -1;
}

// Do not edit the line below.
exports.firstNonRepeatingCharacter = firstNonRepeatingCharacter;
```
