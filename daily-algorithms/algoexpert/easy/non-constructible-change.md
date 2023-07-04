# Non Constructible Change

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 16.00.34.png" alt=""><figcaption></figcaption></figure>

```javascript
function nonConstructibleChange(coins) {
  coins.sort((a, b) => a - b);

  let currentChangeCreated = 0;
  for (const coin of coins) {
    if (coin > currentChangeCreated + 1) return currentChangeCreated + 1;
    currentChangeCreated += coin;
  }
  
  return currentChangeCreated + 1;
}

// Do not edit the line below.
exports.nonConstructibleChange = nonConstructibleChange;
```
