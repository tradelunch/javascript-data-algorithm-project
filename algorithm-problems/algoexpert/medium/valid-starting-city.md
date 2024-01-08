# Valid Starting City

![](<../../../.gitbook/assets/Screenshot 2023-01-24 at 14.04.03.png>)

* n x n, 1

```jsx
function validStartingCity(distances, fuel, mpg) {

  
  for (let i = 0; i < distances.length; i++) {
    let startCity = i;
    let currentCity = i;
    let distanceCanTravel = fuel[currentCity] * mpg - distances[currentCity];
    
    if (distanceCanTravel < 0) continue;

    do {
      currentCity += 1;
      currentCity %= distances.length;
      
      if (currentCity === startCity) return startCity;
      distanceCanTravel += fuel[currentCity] * mpg - distances[currentCity];

    } while (distanceCanTravel >= 0);
    
  }
  
  
  return -1;
}

// Do not edit the line below.
exports.validStartingCity = validStartingCity;
```

* optimized
* n, 1

```jsx
function validStartingCity(distances, fuel, mpg) {
  let totalDistanceTraveled = distances[0];
  let totalFuelCharged = fuel[0] * mpg;
  
  let candidateCity = 0;
  let distanceCanTravel = 0;
  let distanceToFilled = 0;
  for (let i = 1; i < distances.length; i++) {
    totalFuelCharged += fuel[i] * mpg;
    totalDistanceTraveled += distances[i];

    distanceCanTravel += fuel[i - 1] * mpg - distances[i - 1];
    if (distanceCanTravel - distanceToFilled >= 0) continue;

    distanceToFilled = distanceCanTravel;
    candidateCity = i;
  }
  
  if (totalFuelCharged - totalDistanceTraveled < 0)
    return -1;
  
  return candidateCity;
}

// Do not edit the line below.
exports.validStartingCity = validStartingCity;
```
