# Staircase Traversal ⇒ it is like the number of ways to change

![](<../../../.gitbook/assets/Screenshot 2023-01-25 at 1.02.22.png>)

* n, n

```jsx
function staircaseTraversal(height, maxSteps) {
  let cases = new Array(height + 1).fill(0);
  cases[0] = 1;
  
  for (let i = 0; i < height + 1; i++) {
    for (let step = 1; step <= maxSteps; step++) {
      if (step > i) continue;
      cases[i] += cases[i - step];
    }
  }
  
  return cases[height];
}

// Do not edit the line below.
exports.staircaseTraversal = staircaseTraversal;

```
