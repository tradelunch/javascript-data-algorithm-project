# Missing Numbers

![](<../../../.gitbook/assets/Screenshot 2023-04-16 at 16.16.48.png>)

* n, n

```jsx
function missingNumbers(nums) {
  const set = new Set(nums);

  const answer = [];
  for (let i = 1; i <= nums.length + 2; i++) {
    if (set.has(i)) continue;
    answer.push(i);
  }
  
  return answer;
}

// Do not edit the line below.
exports.missingNumbers = missingNumbers;
```

* space optimized: n, 1

```jsx
```
