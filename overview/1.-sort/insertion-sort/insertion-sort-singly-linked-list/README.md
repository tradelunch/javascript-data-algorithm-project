# Insertion Sort:: singly linked list

{% embed url="https://www.algoexpert.io/questions/insertion-sort" %}

<figure><img src="../../../../.gitbook/assets/Screenshot 2023-06-07 at 10.11.10.png" alt=""><figcaption></figcaption></figure>



```javascript
function insertionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    const curr = arr[i];
    for (let j = i - 1; j >= 0; j--) {
      if (arr[j] <= curr) break;
      swap(arr, j, j + 1);
    }
  }

  return arr;
}

function swap(arr, a, b) {
  const temp = arr[a];
  arr[a] = arr[b];
  arr[b] = temp;
}

// Do not edit the line below.
exports.insertionSort = insertionSort;

```





{% embed url="https://leetcode.com/problems/insertion-sort-list/description/" %}



