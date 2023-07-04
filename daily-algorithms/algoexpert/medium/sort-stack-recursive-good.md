# Sort Stack ⇒ recursive good -

![](<../../../.gitbook/assets/Screenshot 2023-02-04 at 20.00.52.png>)

* n^2, n

```tsx
function sortStack(stack) {
  
  takeAllValues(stack);
  return stack;
}

function takeAllValues(stack, idx) {
  if (stack.length === 0) return stack;

  const top = stack.pop();
  takeAllValues(stack);

  sortInOrderAtEachStep(stack, top);
}

function sortInOrderAtEachStep(stack, valueToCompare) {
  if (stack.length === 0 || stack[stack.length - 1] <= valueToCompare) {
    stack.push(valueToCompare);
    return;
  }

  // take top
  const top = stack.pop();

  // sort element inside
  sortInOrderAtEachStep(stack, valueToCompare);

  // push top
  stack.push(top);
  
}

exports.sortStack = sortStack;
```
