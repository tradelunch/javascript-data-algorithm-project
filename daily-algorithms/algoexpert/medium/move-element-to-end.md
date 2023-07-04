# Move Element To End

![](<../../../.gitbook/assets/Screenshot 2023-01-21 at 16.11.38.png>)

* N, 1

```jsx
function moveElementToEnd(arr, toMove) {
  let e = arr.length - 1;
  let s = 0;

  while (s < e) {
    
    while (s < e && arr[e] === toMove) {
      e -= 1;
    }

    if (arr[s] === toMove) {
      [arr[e], arr[s]] = [arr[s], arr[e]];
    }

    s += 1;
  }

  return arr;
}

// Do not edit the line below.
exports.moveElementToEnd = moveElementToEnd;
```
