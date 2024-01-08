# Using Array O(N), O(N)



{% embed url="https://leetcode.com/problems/insertion-sort-list/submissions/965531872/" %}

> time: O(N)
>
> space: O(N)

```javascript
var insertionSortList = function(head) {

    const arr = [];
    let currentNode = head;
    while (currentNode !== null) {
        arr.push(currentNode.val);
        currentNode = currentNode.next;
    }

    for (let i = 0; i < arr.length; i++) {
        const numToSort = arr[i];
        for (let j = i - 1; j >= 0; j--) {
            if (arr[j] <= numToSort) break;
            swap(arr, j, j + 1);
        }
    }

    let idx = 0;
    currentNode = head;
    while (currentNode !== null) {
        currentNode.val = arr[idx++];
        currentNode = currentNode.next;
    }
    
    return head;
};

function swap(arr, a, b) {
    [arr[b], arr[a]] = [arr[a], arr[b]];

}
```

