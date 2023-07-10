# 19. Remove Nth Node From End of List

{% embed url="https://leetcode.com/problems/remove-nth-node-from-end-of-list/" %}





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
 * @param {number} n
 * @return {ListNode}
 */
var removeNthFromEnd = function (head, n) {

    const prev = new ListNode(-1, null);
    prev.next = head;

    let cnt = 0;
    let currentNode = head;
    while (currentNode !== null) {
        currentNode = currentNode.next;
        cnt++;
    }

    currentNode = prev;
    while (cnt - n > 0) {
        console.log(currentNode.val);
        currentNode = currentNode.next;
        cnt--;
    }

    currentNode.next = currentNode.next.next;
    return prev.next;
};
```
