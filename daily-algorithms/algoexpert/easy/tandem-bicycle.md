# Tandem Bicycle

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 19.02.35.png" alt=""><figcaption></figcaption></figure>

```javascript
function tandemBicycle(redShirtSpeeds, blueShirtSpeeds, fastest) {
  redShirtSpeeds.sort((a, b) => a - b);
  blueShirtSpeeds.sort((a, b) => a - b);

  if (fastest === true) {
    blueShirtSpeeds.sort((a, b) => b - a);
  }

  let totalSpeed = 0;
  for (let i = 0; i < redShirtSpeeds.length; i++) {
    const max = Math.max(redShirtSpeeds[i], blueShirtSpeeds[i]);
    totalSpeed += max;
  }
  
  return totalSpeed;
}

// Do not edit the line below.
exports.tandemBicycle = tandemBicycle;
```
