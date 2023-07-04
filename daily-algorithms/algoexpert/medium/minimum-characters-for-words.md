# Minimum Characters For Words

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 15.43.17.png>)



* n \* l, c
* n: number of words, l: longest word, c: the number of unique characters

```tsx
function minimumCharactersForWords(words) {
  const memo = {};

  for (const word of words) {
    
    const temp = {};
    for (const c of word) {
      if (temp[c] === undefined)
        temp[c] = 0;
      temp[c]++;
    }
    for (const c of word) {
      if (memo[c] === undefined)
        memo[c] = 0;
      memo[c] = Math.max(temp[c], memo[c]);
    }
    
  }

  const answer = [];
  for (const [c, count] of Object.entries(memo)) {
    for (let i = 0; i < count; i++) {
      answer.push(c);
    }
  }

  return answer;
}

// Do not edit the line below.
exports.minimumCharactersForWords = minimumCharactersForWords;
```
