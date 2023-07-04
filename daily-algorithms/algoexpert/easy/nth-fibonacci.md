# Nth Fibonacci

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 19.39.26.png" alt=""><figcaption></figcaption></figure>

* n^2, n

```jsx
function getNthFib(n) {
  return fibRecursion(n);
}

function fibRecursion(n) {
  
  if (n === 2) {
    return 1;
  }
  
  if (n === 1) {
    return 0;
  }

  const sum = fibRecursion(n - 1) + fibRecursion(n - 2);
  return sum;
}

// Do not edit the line below.
exports.getNthFib = getNthFib;
```

* n, n
* by removing Nth second recursion

```jsx
let memo = {};
function getNthFib(n) {
  memo = {};
  return fibRecursion(n);
}

function fibRecursion(n) {
  if (memo[n] !== undefined) 
    return memo[n];
  
  if (n === 2) {
    return 1;
  }
  
  if (n === 1) {
    return 0;
  }

  const sum = fibRecursion(n - 1) + fibRecursion(n - 2);
  memo[n] = sum;
  return sum;
}

// Do not edit the line below.
exports.getNthFib = getNthFib;
```

* n, 1

```jsx
function getNthFib(n) {
  let first = 0;
  let second = 1;
  
  while (n > 1) {
    const temp = second;
    second = first + second;
    first = temp;
    n--;
  }

  return first;
}

// Do not edit the line below.
exports.getNthFib = getNthFib;
```
