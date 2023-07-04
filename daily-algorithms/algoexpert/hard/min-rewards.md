# Min Rewards

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 14.42.41.png>)

* n^2, n

```jsx
function minRewards(scores) {
  const rewards = new Array(scores.length).fill(1);

  for (let i = 1; i < scores.length; i++) {
    if (scores[i - 1] < scores[i]) {
      rewards[i] = rewards[i - 1] + 1;
      continue;
    }

    let j = i - 1;
    while (j >= 0 && scores[j] > scores[j + 1]) {
      rewards[j] = Math.max(rewards[j], rewards[j + 1] + 1);
      j--;
    }
    
  }
  
  let sum = 0;
  for (let i = 0; i < rewards.length; i++) {
    sum += rewards[i];
  }
  
  return sum;
}
```

* optimized
* n, n

```jsx
function minRewards(arr) {
  const rewards = new Array(arr.length).fill(1);

  for (let i = 1; i < arr.length; i++) {
    if (arr[i - 1] >= arr[i]) continue;
    rewards[i] = rewards[i - 1] + 1;
  }

  for (let i = arr.length - 2; i >= 0; i--) {
    if (arr[i] <= arr[i + 1]) continue;
    rewards[i] = Math.max(rewards[i], rewards[i + 1] + 1);
  }

  let sum = 0;
  for (let num of rewards) {
    sum += num;
  }
  console.log({
    rewards
  })
  return sum;
}

// 3 2 1 10 11 6 5 4

// Do not edit the line below.
exports.minRewards = minRewards;
```
