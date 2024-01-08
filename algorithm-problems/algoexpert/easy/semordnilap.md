# Semordnilap

![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 21.26.42.png>)

* N\*W (W is the longest word), N

```jsx
function semordnilap(words) {
  const answer = [];
  const memo = {}
  for (const word of words) {
    if (memo[word] !== undefined) {
      answer.push([word, reverse(word)]);
      continue;
    }

    memo[reverse(word)] = word;
  }
  
  return answer;
}

function reverse(word) {
  word = word.split('');

  let s = 0;
  let e = word.length - 1;
  while (s <= e) {
    [word[e], word[s]] = [word[s], word[e]];
    s++;
    e--;
  }

  return word.join('');
}

// Do not edit the line below.
exports.semordnilap = semordnilap;

```
