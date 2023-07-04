# Three Number Sort ⇒ counting sort or radix sort ⇒ three pointer with in-place swap

![](<../../../.gitbook/assets/Screenshot 2023-01-25 at 1.13.48.png>)

* n x m, 1

```jsx
function threeNumberSort(arr, order) {

  let pointer = 0;
  for (const target of order) {
    
    for (let i = pointer; i < arr.length; i++) {
      const curr = arr[i];
      if (target !== curr) continue;
      swap(arr, pointer, i);
      pointer++;
    }
    
  }

  return arr;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
  return arr;
}

// Do not edit the line below.
exports.threeNumberSort = threeNumberSort;
```

* faster?
* with only 3 numbers?
* three pointers
* n, 1

```jsx
function threeNumberSort(arr, order) {
  
  const pointers = [0, 0, 0];
  for (let i = 0; i < arr.length; i++) {
    
    const curr = arr[i];
    if (curr === order[0]) {
      pointers[0]++;
      pointers[1]++;
      pointers[2]++;
    } else if (curr === order[1]) {
      pointers[1]++;
      pointers[2]++;
    } else {
      pointers[2]++;
    }
    
  }

  for (let i = 0; i < arr.length; i++) {
    
    if (i < pointers[0]) {
      arr[i] = order[0];
    } else if (i < pointers[1]) {
      arr[i] = order[1];
    } else {
      arr[i] = order[2];
    }
    
  }

  return arr;
}

function swap(arr, a, b) {
  [arr[b], arr[a]] = [arr[a], arr[b]];
  return arr;
}

// Do not edit the line below.
exports.threeNumberSort = threeNumberSort;
```

* 3rd try
* iteration - in place swap

```jsx
function threeNumberSort(arr, order) {
  let f = 0;
  let s = 0;
  let e = arr.length - 1;
  while (s <= e) {
    const curr = arr[s];

    if (curr === order[0]) {

      swap(arr, f, s);
      f++;
      s++;
    } else if (curr === order[1]) {
      s++;
    } else {
      swap(arr, e, s);
      e--;
    }  
  }
  
  return arr;
}

function swap(arr, a, b) {
  [arr[a], arr[b]] = [arr[b], arr[a]];
  return arr;
}

// Do not edit the line below.
exports.threeNumberSort = threeNumberSort;
```
