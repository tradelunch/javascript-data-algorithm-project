# Max Path Sum In Binary Tree

![](<../../../.gitbook/assets/Screenshot 2023-02-12 at 21.26.18.png>)

* h, h

```jsx
function maxPathSum(tree) {

  const max = {
    sum: -Infinity,
  };

  findMaxSum(tree, max);
  return max.sum;
}

function findMaxSum(node, max) {
  if (node === null) {
    return 0;
  }

  const left = findMaxSum(node.left, max);
  const right = findMaxSum(node.right, max);

  const currentValue = node.value;
  const pathMax = left + right + node.value;
  max.sum = Math.max(max.sum, pathMax, currentValue, left + currentValue, right + currentValue);
  
  return Math.max(left, right) + currentValue;
}

exports.maxPathSum = maxPathSum;
```
