# Levenshtein Distance

![](<../../../.gitbook/assets/Screenshot 2023-01-22 at 23.35.47.png>)

* n x m, n x m

```jsx
function levenshteinDistance(str1, str2) {
  const edits = new Array(str1.length + 1);
  edits[0] = new Array(str2.length + 1).fill(1).map((v, idx) => idx)
  for (let i = 1; i < str1.length + 1; i++ ) {
    edits[i] = new Array(str2.length + 1).fill(0);
    edits[i][0] = i;
  }

  for (let i = 1; i < str1.length + 1; i++) {
    for (let j = 1; j < str2.length + 1; j++) {
      const c1 = str1[i - 1];
      const c2 = str2[j - 1];

      if (c1 === c2) {
        edits[i][j] = edits[i - 1][j - 1];
        continue;
      }

      edits[i][j] = Math.min(edits[i - 1][j], edits[i][j - 1], edits[i - 1][j - 1]) + 1;
    }
  }
  console.log(edits)

  return edits[str1.length][str2.length];
}

// Do not edit the line below.
exports.levenshteinDistance = levenshteinDistance;
```

* n x m, min(m, n)

```jsx
function levenshteinDistance(str1, str2) {
  let small = str1;
  let big = str2;
  if (small.length > big.length) {
    const temp = small;
    small = big;
    big = temp;
  }

  // set up two arrays 
  const evenEdits = new Array(small.length + 1);
  for (let i = 0; i < evenEdits.length; i++) {
    evenEdits[i] = i;
  }
  const oddEdits = new Array(small.length + 1).fill(0);

  let previousEdits = [0]; // when empty
  let currentEdits = [0]; // when empty
  
  for (let i = 1; i < big.length + 1; i++) {
    // swap edits array
    if (i % 2 === 1) {
      previousEdits = evenEdits;
      currentEdits = oddEdits;
    } else {
      previousEdits = oddEdits;
      currentEdits = evenEdits;
    }

    currentEdits[0] = i;
    
    for (let j = 1; j < small.length + 1; ++j) {
      if (big[i - 1] === small[j - 1]) {
        currentEdits[j] = previousEdits[j - 1];
      } else {
        currentEdits[j] = 1 + Math.min(currentEdits[j - 1], previousEdits[j], previousEdits[j - 1])
      }
    }
    
  }
  
  return currentEdits[small.length];
}

// Do not edit the line below.
exports.levenshteinDistance = levenshteinDistance;
```
