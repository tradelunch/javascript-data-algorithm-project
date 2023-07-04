# Palindrome Check





![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 20.42.21.png>)

```javascript
function isPalindrome(string) {
  let s = 0
  let e = string.length - 1;
  while (s <= e) {
    if (string[s] !== string[e]) return false;
    s++;
    e--;
  }

  return true;
}

// Do not edit the line below.
exports.isPalindrome = isPalindrome;
```
