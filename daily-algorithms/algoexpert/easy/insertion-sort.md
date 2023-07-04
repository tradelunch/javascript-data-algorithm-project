# Insertion Sort

<figure><img src="../../../.gitbook/assets/Screenshot 2023-01-20 at 21.29.07.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/insertion-sort-graphic.gif" alt=""><figcaption></figcaption></figure>

* best: N, 1
* average, worst: N^2, 1
* swap last

```jsx
function insertionSort(arr) {
	for (let i = 1; i < arr.length; i++) {
		const curr = arr[i];
		let idx = i;
		while (idx >= 1) {
			if (curr >= arr[idx - 1]) break; // vale at curr i, has to be compared with all previous values
			arr[idx] = arr[idx - 1]; // move backward by 1 step
			idx--;
		}
		arr[idx] = curr;
	}

	return arr;
}

function swap(arr, a, b) {
	[arr[b], arr[a]] = [arr[a], arr[b]];
}
// Do not edit the line below.
exports.insertionSort = insertionSort;
```

* swap every time

```jsx
function insertionSort(arr) {
	for (let i = 1; i < arr.length; i++) {
		const curr = arr[i];
		let idx = i;
		while (idx >= 1) {
			if (curr >= arr[idx - 1]) break; // vale at curr i, has to be compared with all previous values
			swap(arr, idx, idx - 1);
			idx--;
		}
	}

	return arr;
}

function swap(arr, a, b) {
	[arr[b], arr[a]] = [arr[a], arr[b]];
}
// Do not edit the line below.
exports.insertionSort = insertionSort;
```

* simple

```jsx
function insertionSort(arr) {
  
  for (let i = 1; i < arr.length; i++) {
    // const base = arr[i];
    let idx = i;
    while (idx > 0) {
      if (arr[idx - 1] <= arr[idx]) break;
      [arr[idx - 1], arr[idx]] = [arr[idx], arr[idx - 1]];
      idx--;
    }
    
  }
  
  return arr;
}

// Do not edit the line below.
exports.insertionSort = insertionSort;
```
