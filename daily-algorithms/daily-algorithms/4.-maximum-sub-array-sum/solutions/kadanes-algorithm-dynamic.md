# Kadane's Algorithm - Dynamic

{% embed url="https://zerobone.net/blog/cs/kadane-algorithm/" %}

{% embed url="https://sustainable-dev.tistory.com/23" %}

{% embed url="https://leetcode.com/problems/maximum-subarray/submissions/964826288/" %}

<figure><img src="../../../../.gitbook/assets/kadane-algorithm-tmb (1).jpg" alt=""><figcaption></figcaption></figure>

```javascript
var maxSubArray = function(nums) {
    let maxSum = -Infinity;
    let currSum = 0;

    for (let i = 0; i < nums.length; i++) {
      const curr = nums[i];
      currSum = Math.max(curr, currSum + curr);
      maxSum = Math.max(maxSum, currSum);
    }

    return maxSum;
};
```





