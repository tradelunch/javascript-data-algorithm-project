# 143. Reorder List

{% embed url="https://leetcode.com/problems/reorder-list/" %}

> time: O(n)

> space: O(1)

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {void} Do not return anything, modify head in-place instead.
 */
var reorderList = function (head) {

    let slow = head;
    let fast = head;

    while (fast.next !== null && fast.next.next !== null) {
        slow = slow.next;
        fast = fast.next.next;
    }

    let prev = null;
    let curr = slow.next;
    while (curr !== null) {
        const next = curr.next;
        curr.next = prev;
        prev = curr;
        curr = next;
    }
    slow.next = null;

    curr = head;
    while (prev !== null) {
        const next = curr.next;
        const prevNext = prev.next;
        curr.next = prev;
        prev.next = next;

        curr = next;
        prev = prevNext;
    }

    return head;
};
```

