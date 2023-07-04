# Monotonic Array

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-21 at 16.13.20.png" alt=""><figcaption></figcaption></figure>

* N, 1

```jsx
function isMonotonic(arr) {
  // -1: down, 0: undefined, 1: up
  let flag = 0; 

  let prev = 0;
  let curr = 0;
  while (curr < arr.length) {

    if (arr[prev] > arr[curr]) {
      if (flag === 1) return false;
      if (flag === 0) flag = -1;
    }
    
    if (arr[prev] < arr[curr]) {
      if (flag === -1) return false;
      if (flag === 0) flag = 1;
    }

    prev = curr;
    curr++;
  }
  
  return true;
}

// Do not edit the line below.
exports.isMonotonic = isMonotonic;
```

* simple

```jsx
function isMonotonic(arr) {
	let isIncreasing = false;
	let isDescreasing = false;
	
	let idx = 1;
	while (idx < arr.length) {
      if (arr[idx - 1] < arr[idx]) isIncreasing = true;
      if (arr[idx - 1] > arr[idx]) isDescreasing = true; 
      idx++;
	}
  
  return !isDescreasing || !isIncreasing;
}

// Do not edit the line below.
exports.isMonotonic = isMonotonic;
```
