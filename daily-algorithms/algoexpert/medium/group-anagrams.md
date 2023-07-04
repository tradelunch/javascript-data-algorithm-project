# Group Anagrams

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 14.11.18.png>)

* w \* nlogn, w \* n

```tsx
function groupAnagrams(words) {

  const map = {};
  
  for (let i = 0; i < words.length; i++) {
    const word = words[i];
    const sorted = [...word].sort().join('');

    if (map[sorted] === undefined)
      map[sorted] = [];

    map[sorted].push(word);
  }

  return Object.values(map);
  
}

// Do not edit the line below.
exports.groupAnagrams = groupAnagrams;
```
