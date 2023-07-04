# Valid IP Addresses

![](<../../../.gitbook/assets/Screenshot 2023-02-05 at 14.27.30.png>)

* 1, 1 why? a length of string is always less than or equal to 12

```tsx
function validIPAddresses(str) {

  if (str.length < 4) return [];
  if (str.length > 12) return [];

  const answer = [];
  for (let i = 1; i < 4; i++) {
    const first = str.slice(0, i);
    if (!isValidPart(first)) continue;

    
    for (let j = i + 1; j < i + 4; j++) {
      const second = str.slice(i, j);
      if (!isValidPart(second)) continue;
      
      for (let k = j + 1; k < j + 4; k++) {
        const third = str.slice(j, k);
        if (!isValidPart(third)) continue;
        
        const fourth = str.slice(k);
        if (!isValidPart(fourth)) continue;
        
        answer.push([first, second, third, fourth].join('.'));
        
      }
      
    }
    
  }
  
  return answer;
}

function isValidPart(str) {
  if (str.length === 0) return false;
  if (str.length > 3) return false;
  if (str.length > 1 && str[0] === '0') return false;
  if (Number(str) > 255) return false;
  return true;
}

// Do not edit the line below.
exports.validIPAddresses = validIPAddresses;
```
