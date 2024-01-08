# Min Number Of Coins For Change

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 23.21.20.png>)

* n, n

```jsx
function minNumberOfCoinsForChange(n, denoms) {
  denoms.sort((a, b) => a - b);
  const coins = new Array(n + 1).fill(Infinity);
  coins[0]= 0;

  for (const denom of denoms) {
    for (let i = 1; i < n + 1; i++) {
      if (denom > i) continue;
      coins[i] = Math.min(coins[i], coins[i - denom] + 1);
    }
  }

  return coins[n] === Infinity ? -1 : coins[n];
}

// Do not edit the line below.
exports.minNumberOfCoinsForChange = minNumberOfCoinsForChange;
```
