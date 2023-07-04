# Generate Document

![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 21.11.33.png>)

* n, 1 (only 26 alphabet)

```jsx
function generateDocument(characters, document) {
  const frequency = {};
  for (const c of characters) {
    if (frequency[c] === undefined) frequency[c] = 0;
    frequency[c] += 1;
  }

  console.log({
    frequency
  });

  for (const c of document) {
    if (frequency[c] === undefined || frequency[c] === 0) return false;
    frequency[c] -= 1;
  }
  
  return true;
}

// Do not edit the line below.
exports.generateDocument = generateDocument;
```
