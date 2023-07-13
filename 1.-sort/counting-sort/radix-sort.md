# Radix Sort

[Radix Sort](https://lktprogrammer.tistory.com/)



{% embed url="https://www.algoexpert.io/questions/radix-sort" %}



with just use array

```javascript
function radixSort(arr) {
  const max = Math.max(...arr);
  let digit = 0;
  while (10 ** digit <= max) {
    sort(arr, digit);
    digit++;
  }
  
  return arr;
}

function sort(arr, digit) {

  const bucket = new Array(10);
  for (let i = 0; i < arr.length; i++) {
    const curr = Number.parseInt(arr[i] / (10 ** digit));
    const mod = curr % 10;
    if (bucket[mod] === undefined) bucket[mod] = [];
    bucket[mod].push(arr[i]);
  }


  let idx = 0;
  for (let i = 0; i < bucket.length; i++) {
    const subArr = bucket[i] ?? [];
    for (const curr of subArr) {
      arr[idx] = curr;
      idx++;
    }
  }
  
  return arr;
}

// Do not edit the line below.
exports.radixSort = radixSort;

```





with index

```javascript
function radixSort(arr) {
  
  const max = Math.max(...arr);

  let digit = 0;
  while (10 ** digit <= max) {
    sortArray(arr, digit);
    digit++;
  }
  
  return arr;
}

function sortArray(arr, digit) {

  const indexes = new Array(10).fill(0);

  for (let i = 0; i < arr.length; ++i) {
    const curr = arr[i];
    let digitNum = Math.floor(curr / (10 ** digit));
    digitNum = digitNum % 10;
    indexes[digitNum]++;
  }

  for (let i = 1; i < 10; ++i) {
    indexes[i] += indexes[i - 1];
  }

  const sortedArr = new Array(arr.length).fill(0);
  for (let i = arr.length - 1; i >= 0; --i) {
    const curr = arr[i];
    let digitNum = Math.floor(curr / (10 ** digit));
    digitNum = digitNum % 10;
    indexes[digitNum]--;
    
    const currentIndex = indexes[digitNum];
    sortedArr[currentIndex] = curr;
  }

  for (let i = 0; i < arr.length; ++i) {
    arr[i] = sortedArr[i];
  }
  
  return arr;
}

// Do not edit the line below.
exports.radixSort = radixSort;

```



