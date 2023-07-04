# Largest Range

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 14.12.50 (1).png>)

* nlog, 1

```jsx
function largestRange(arr) {
  arr.sort((a, b) => a - b);
  console.log({ arr });
  
  let max = [arr[0], arr[0]];
  let range = [arr[0], arr[0]];
  
  for (let i = 1; i < arr.length; i++) {
    // same or diff is 1
    if (arr[i] - arr[i - 1]  <= 1) {
      // extend
      range[1] = arr[i];    
      continue;
    }
    console.log({
      range
    });

    // update
    const curr = Math.abs(max[1] - max[0]);
    const next = Math.abs(range[1] - range[0]);
    if (curr < next) {
      max = range;
    }

    // default
    range = [arr[i], arr[i]];
  }

      // update
  const curr = Math.abs(max[1] - max[0]);
  const next = Math.abs(range[1] - range[0]);
  if (curr < next) {
    max = range;
  }

  return max;
}

// Do not edit the line below.
exports.largestRange = largestRange;
```

* n, n

```jsx
function largestRange(arr) {
  let longestRange = [arr[0], arr[0]];
  
  const nums = [];
  for (const num of arr) {
    nums[num] = true;
  }

  // O(N) cuz when visted, we do not check anymore
  for (const num of arr) {
    // check if visited before
    if(!nums[num]) continue;
    nums[num] = false; // visited

    const currentRnage = [num, num];

    // find left
    let left = num - 1;
    while (nums[left]) {
      nums[left] = false; // visited
      currentRnage[0] = left;
      left--;
    }

    // find right
    let right = num + 1;
    while (nums[right]) {
      nums[right] = false; // visited
      currentRnage[1] = right;
      right++;
    }

    // check diff btw
    if (getAbsDiff(longestRange) >= getAbsDiff(currentRnage)) continue;

    // currentRage > longestRange
    longestRange = currentRnage;
  }

  return longestRange;
}

function getAbsDiff(arr) {
  return Math.abs(arr[1] - arr[0]);
}

// Do not edit the line below.
exports.largestRange = largestRange;
```
