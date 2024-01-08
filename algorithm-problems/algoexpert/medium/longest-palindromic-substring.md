# Longest Palindromic Substring

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 13.10.37.png>)

* n^2, n

```tsx
function longestPalindromicSubstring(str) {

  let longest = [0, 1];
  
  for (let i = 0; i < str.length - 1; i++) {
    
    const odd = getLongestPalindrome(str, i, i);
    const even = getLongestPalindrome(str, i, i + 1);
    const current = odd[1] - odd[0] > even[1] - even[0] ? odd : even;
    longest = current[1] - current[0] > longest[1] - longest[0] ? current : longest;
  }

  return str.slice(longest[0], longest[1]);
  
}

function getLongestPalindrome(str, s, e) {

  while (s >= 0 && e < str.length) {
    if (str[s] !== str[e]) break;
    s--;
    e++;
  }

  return [s + 1, e];
}

function isPalidrome(str, s, e) {
  
  while (s <= e) {
    if (str[s] !== str[e]) 
      return false;
    s++;
    e--;
  }

  return true;
}

// Do not edit the line below.
exports.longestPalindromicSubstring = longestPalindromicSubstring;
```
