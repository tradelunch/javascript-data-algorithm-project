# Divide And Conquer



<figure><img src="../../../../.gitbook/assets/max sub array sum divide and conquer (1).png" alt=""><figcaption><p>pic is wrong</p></figcaption></figure>

{% embed url="https://leetcode.com/problems/maximum-subarray/submissions/964872776/" %}



```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function(nums) {
    return maxSubArraySum(nums, 0, nums.length - 1);
};

function maxSubArraySum(arr, left, right) {
    if (left === right) return arr[left];

    const mid = left + Math.floor((right - left) / 2);

    const leftMax = maxSubArraySum(arr, left, mid);
    const rightMax = maxSubArraySum(arr, mid + 1, right);
    const crossMax = maxCrossSum(arr, mid, left, right);

    return Math.max(leftMax, rightMax, crossMax);
}

function maxCrossSum(arr, mid, left, right) {

    // left
    let leftMaxSum = -Infinity;
    let leftSum = 0;
    for (let i = mid; i >= left; i--) {
        const curr = arr[i];
        leftSum += curr;
        leftMaxSum = Math.max(leftMaxSum, leftSum);        
    }

    // right
    let rightMaxSum = -Infinity;
    let rightSum = 0;
    for (let i = mid + 1; i <= right; i++) {
        const curr = arr[i];
        rightSum += curr;
        rightMaxSum = Math.max(rightMaxSum, rightSum);
    }

    return leftMaxSum + rightMaxSum;
}
```



