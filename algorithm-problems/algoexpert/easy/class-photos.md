# Class Photos

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 18.57.59.png" alt=""><figcaption></figcaption></figure>

```javascript
function classPhotos(redShirtHeights, blueShirtHeights) {
  redShirtHeights.sort((a, b) => b - a);
  blueShirtHeights.sort((a, b) => b - a);

  let front = redShirtHeights;
  let back = blueShirtHeights;
  if (front[0] > back[0]) {
    front = blueShirtHeights;
    back = redShirtHeights;
  }

  for (let i = 0; i < front.length; i++) {
    if (front[i] < back[i]) continue;
    return false;
  }
  
  return true;
}

// Do not edit the line below.
exports.classPhotos = classPhotos;
```
