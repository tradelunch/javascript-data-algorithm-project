# Caesar Cipher Encryptor

![](<../../../.gitbook/assets/Screenshot 2023-01-20 at 20.51.56.png>)



* n, n

```jsx
const alphabet = `abcdefghijklmnopqrstuvwxyz`;
const aCode = alphabet.charCodeAt(0);
function caesarCipherEncryptor(str, key) {
  const answer = [];
  for (let i = 0; i < str.length; i++) {
    let code = str.charCodeAt(i) - aCode;
    code += key;
    code %= 26;
    answer.push(alphabet[code]);
  }

  return answer.join('');
}

// Do not edit the line below.
exports.caesarCipherEncryptor = caesarCipherEncryptor;
```
