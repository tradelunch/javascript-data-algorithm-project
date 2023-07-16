# 300. Longest Increasing Subsequence



{% embed url="https://leetcode.com/problems/longest-increasing-subsequence/" %}

just max sub array length

> time: O(n^2)

> space: O(n)

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
    const len = new Array(nums.length);
    for (let i = 0; i < nums.length; i++) {
        len[i] = 1;
    }

    let max = 1;
    for (let i = 1; i < nums.length; i++) {
        for (let j = i - 1; j >= 0; j--) {
            if (nums[j] < nums[i]) {
                len[i] = Math.max(len[j] + 1, len[i]);
            }
        }
        max = Math.max(max, len[i]);
    }

    return max;
};
```

with path

```jsx
/**
 * @param {number[]} nums
 * @return {number}
 */
var lengthOfLIS = function(nums) {
    const id = new Array(nums.length); // [[parentIndex, length]]
    const len = new Array(nums.length);
    for (let i = 0; i < nums.length; i++) {
        id[i] = i;
        len[i] = 1;
    }

    for (let i = 1; i < nums.length; i++) {
        const curr = nums[i];
        for (let j = i - 1; j >= 0; j--) {
            if (nums[j] < nums[i]) {
                if (len[j] + 1 > len[i]) {
                    id[i] = j;
                    len[i] = len[j] + 1;
                }
            }
        }
    }

    let max = 1;
    for (let i = 0; i < nums.length; i++) {
        max = Math.max(max, len[i]);
    }

    return max;
};
```



