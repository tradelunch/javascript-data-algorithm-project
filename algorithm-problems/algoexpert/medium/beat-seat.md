# Beat Seat

<figure><img src="../../../.gitbook/assets/Screenshot 2023-04-15 at 20.29.17.png" alt=""><figcaption></figcaption></figure>

* n, 1

```jsx
function bestSeat(seats) {

  let s = 0;
  let e = 0;

  let seat = [-1, -1];
  while (e < seats.length) {
    let left = seats[s];
    let right = seats[e];

    if (left === 1) {
      s++;
      e++;
      continue;
    }

    if (right === 1) {
      const [m, length] = calcSeat(s, e - 1);
      if (seat[1] < length) {
        seat = [m, length];
      }
      
      s = e;
      e += 1;
      continue;
    }

    e++;
  }
  
  return seat[0];
}

const calcSeat = (s, e) => {
  return [s + Math.floor((e - s) / 2), e - s];
}

// Do not edit the line below.
exports.bestSeat = bestSeat;
```

```jsx
function bestSeat(seats) {

  let beatSeat = 0;
  let maxSeats = 0;

  let left = 0;
  while (left < seats.length) {
    let right = left + 1;
    while (right < seats.length && seats[right] === 0) {
      right++;
    }

    const availableSeats = right - left - 1;
    if (maxSeats < availableSeats) {
      beatSeat = left + Math.floor((right - left) / 2);
      maxSeats = availableSeats;
    }

    left = right;
  }

  
  return beatSeat;
}

// Do not edit the line below.
exports.bestSeat = bestSeat;
```
