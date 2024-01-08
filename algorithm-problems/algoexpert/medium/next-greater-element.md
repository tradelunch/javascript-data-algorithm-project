# Next Greater Element

![](<../../../.gitbook/assets/Screenshot 2023-02-04 at 20.53.07.png>)

* n^2, n

```tsx
function nextGreaterElement(arr) {

  const answer = [];

  for (let i = 0; i < arr.length; i++) {
    const curr = i;
    let idx = (i + 1) % arr.length;
    
    while (idx !== i) {

      if (arr[curr] < arr[idx]) {
        answer[curr] = arr[idx];
        break;
      }
      idx++;
      idx %= arr.length;      
    }
    
    if (idx === i) {
      answer[curr] = -1;
    }
    
  }
  
  return answer;
}

// Do not edit the line below.
exports.nextGreaterElement = nextGreaterElement;
```

* optimized with using stack ⇒ pick from latest element
* n, n

```tsx
function nextGreaterElement(arr) {
  const answer = new Array(arr.length).fill(-1);
  
  const len = arr.length * 2;
  const stack = [];
  for (let i = len - 1; i >= 0; --i) {
    const idx = i % arr.length;
    const currentValue = arr[idx];

    while (stack.length > 0) {
      
      if (stack[stack.length -1 ] <= currentValue) {
        const top = stack.pop();
      } else {
        answer[idx] = stack[stack.length - 1];
        break;
      }
    }
    
    
    stack.push(currentValue);
  }
  
  return answer;
}

// Do not edit the line below.
exports.nextGreaterElement = nextGreaterElement;
```
