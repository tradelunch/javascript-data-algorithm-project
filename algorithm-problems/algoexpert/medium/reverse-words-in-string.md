# Reverse Words in String

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 14.27.30.png>)

* n, n

```tsx
function reverseWordsInString(str) {

  const arr = [];
  let word = [];
  for (let i = 0; i < str.length; i++) {
    const curr = str[i];
    if (curr !== ' ') {
      word.push(curr);
      continue;
    }
    
    arr.unshift(...word);
    arr.unshift(curr)
    word = [];
  }

  if (word.length > 0) 
    arr.unshift(...word);

  return arr.join('');
}

// Do not edit the line below.
exports.reverseWordsInString = reverseWordsInString;
```
