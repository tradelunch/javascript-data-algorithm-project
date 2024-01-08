# Phone Number Mnemonics ⇒ can use word and index to create each case without concatenation

![](<../../../.gitbook/assets/Screenshot 2023-01-25 at 0.30.03.png>)



* first try
* time: 4^n x n
  * n: length of phonenumber
  * each number ⇒ has max 4 different cases ⇒ each case run
    * n- 1, n - 2, …. ⇒ n
    * each time 4^n happens
* space: 4^n cases, each case has length of n

concat part increase time

```jsx
const keypad = {
  0: '0',
  1: '1',
  2: 'abc',
  3: 'def',
  4: 'ghi',
  5: 'jkl',
  6: 'mno',
  7: 'pqrs',
  8: 'tuv',
  9: 'wxyz',
};

let mnemonics;
function phoneNumberMnemonics(phoneNumber) {
  mnemonics = [];
  buildMnemonic(phoneNumber);
  return mnemonics;
}

function buildMnemonic(phoneNumber, idx = 0, curr = []) {
  if (phoneNumber.length === curr.length) {
    mnemonics.push(curr.join(''));
    return;
  }

  const number = Number(phoneNumber[idx]);
  const chars = keypad[number];

  for (let i = 0; i < chars.length; i++) {
    buildMnemonic(phoneNumber, idx + 1, curr.concat(chars[i]));
  }

  return;
}

// Do not edit the line below.
exports.phoneNumberMnemonics = phoneNumberMnemonics;
```

* second try
* removed concat

using word and its index to store each letter,

* 4^n x n, 4^n x n

```jsx
const keypad = {
  0: '0',
  1: '1',
  2: 'abc',
  3: 'def',
  4: 'ghi',
  5: 'jkl',
  6: 'mno',
  7: 'pqrs',
  8: 'tuv',
  9: 'wxyz',
};

let mnemonics;
function phoneNumberMnemonics(phoneNumber) {
  const word = new Array(phoneNumber.length).fill('0');
  mnemonics = [];
  buildMnemonic(phoneNumber, 0, word);
  return mnemonics;
}

function buildMnemonic(phoneNumber, idx = 0, word = []) {
  if (phoneNumber.length === idx) {
    mnemonics.push(word.join(''));
    return;
  }

  const number = Number(phoneNumber[idx]);
  const chars = keypad[number];

  for (let i = 0; i < chars.length; i++) {
    word[idx] = chars[i];
    buildMnemonic(phoneNumber, idx + 1, word);
  }

  return;
}

// Do not edit the line below.
exports.phoneNumberMnemonics = phoneNumberMnemonics;
```
