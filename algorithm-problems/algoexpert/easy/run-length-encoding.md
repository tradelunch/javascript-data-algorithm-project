# Run Length Encoding





* n, 1

```jsx
function runLengthEncoding(str) {
  let answer = '';
  let prev = str[0];
  let count = 1;
  for (let i = 1; i < str.length; i++) {
    const curr = str[i];
    // when to print?
    // when count === 9 or prev !== current;
    if (prev !== curr || count === 9) {
      answer += count;
      answer += prev;
      prev = curr;
      count = 0;
    }
    
    count++;
  }

  answer += count;
  answer += prev;

  return answer;
}

// Do not edit the line below.
exports.runLengthEncoding = runLengthEncoding;
```
