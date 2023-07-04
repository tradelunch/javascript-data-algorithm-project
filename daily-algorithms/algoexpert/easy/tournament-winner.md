# Tournament Winner

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 15.43.28.png" alt=""><figcaption></figcaption></figure>

```javascript
function tournamentWinner(competitions, results) {
  const scores = {};
  
  let max = ['', -Infinity];
  let idx = 0;
  while (idx < results.length) {
    const [home, away] = competitions[idx]; // 1 home, 0 away
    const result = results[idx];

    let team = home;
    if (result === 0)
      team = away;
    
    if (scores[team] === undefined)
      scores[team] = 0;
    scores[team] += 3;
    
    if (scores[team] > max[1])
      max = [team, scores[team]];
    
    idx++;

  }
  
  return max[0];
}

// Do not edit the line below.
exports.tournamentWinner = tournamentWinner;
```

