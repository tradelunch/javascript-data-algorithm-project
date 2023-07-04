# Stable Internships

![](<../../../.gitbook/assets/Screenshot 2023-01-23 at 19.08.38.png>)

* n \* n (when building teamToInternRank), n ()

```jsx
// preference priority
function stableInternships(interns, teams) {
  // return [[internIndex, teamIndex]]

  const teamToInternRank = {};
  for (let i = 0; i < teams.length; i++) {
    teamToInternRank[i] = [];
    
    const teamPreference = teams[i];
    for (let j = 0; j < teamPreference.length; j++) {
      const intern = teamPreference[j];
      teamToInternRank[i][intern] = j;
    }
  }

  const internPotentialTeamIndices = new Array(interns.length).fill(0);
  const teamToInternMatched = {};

  const internsInSelecting = [];
  for (let i = 0; i < interns.length; i++) {
    internsInSelecting.push(i);
  }
  
  while (internsInSelecting.length > 0) {
    const internCurrent = internsInSelecting.pop();
    
    const potentialTeamIndex = internPotentialTeamIndices[internCurrent];
    const teamInternCurrentPrefer = interns[internCurrent][potentialTeamIndex];
    
    internPotentialTeamIndices[internCurrent] += 1; 
    

    // check team above has a chosen intern now
    // no
    if (teamToInternMatched[teamInternCurrentPrefer] === undefined) {
      teamToInternMatched[teamInternCurrentPrefer] = internCurrent;
      continue;
    }

    // yes
    const teamPrefer = teamToInternRank[teamInternCurrentPrefer];
    const internMatched = teamToInternMatched[teamInternCurrentPrefer];
    // check if which intern, a teamInternCurrentPrefer like more
    if (teamPrefer[internCurrent] >= teamPrefer[internMatched]) {
      internsInSelecting.push(internCurrent);
      continue;
    } 

    teamToInternMatched[teamInternCurrentPrefer] = internCurrent;
    internsInSelecting.push(internMatched);
  }

  const answer = 
    Object.entries(teamToInternMatched)
    .map(([team, intern]) => [Number(intern), Number(team)]);
  
  return answer;
}

// Do not edit the line below.
exports.stableInternships = stableInternships;
```
