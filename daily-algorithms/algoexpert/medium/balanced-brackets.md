# Balanced Brackets

![](<../../../.gitbook/assets/Screenshot 2023-02-04 at 16.10.55.png>)



* n, n

```tsx
// ()

const map = {
  ')': '(',
  '}': '{',
  ']': '['
};

const set = new Set([')', '(', '}', '{', ']', '[']);

function balancedBrackets(str) {

  const stack = [];

  for (let i = 0; i < str.length; i++) {
    const curr = str[i];

    if (!set.has(curr)) continue;
    
    if (curr === '(' || curr === '{' || curr === '[') {
      stack.push(curr);
      continue;
    }

    const top = stack.pop();
    if (top === undefined) return false;
    if (map[curr] !== top) return false;
    
  }

  if (stack.length > 0) return false;

  return true;

}

// Do not edit the line below.
exports.balancedBrackets = balancedBrackets;
```
