# Evaluate Expression Tree



![](<../../../.gitbook/assets/Screenshot 2023-04-15 at 16.53.41.png>)

* n, h

```jsx
// This is an input class. Do not edit.
class BinaryTree {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

const add = (a, b) => a + b;
const subtract = (a, b) => a - b;
const divide = (a, b) => a / b;
const multiply = (a, b) => a * b;

const operations = {
  '-1': add,
  '-2': subtract,
  '-3': divide,
  '-4': multiply
}

function evaluateExpressionTree(tree) {

  return evaluate(tree);
}

function evaluate(node) {
  if (node.value > 0) 
    return node.value;

  const operator = node.value;
  const operate = operations[operator];
  
  const left = evaluate(node.left);
  const right = evaluate(node.right);

  return parseInt(operate(left, right));
}

// Do not edit the lines below.
exports.BinaryTree = BinaryTree;
exports.evaluateExpressionTree = evaluateExpressionTree;
```
