# Brute Force



{% embed url="https://leetcode.com/problems/maximum-subarray/submissions/964852439/" %}

```javascript

var maxSubArray = function(nums) {
    let maxSum = -Infinity;

    for (let i = 0; i < nums.length; i++) {
      
      let currSum = 0;
      for (let j = i; j < nums.length; j++) {
        currSum += nums[j];
        maxSum = Math.max(currSum, maxSum);
      }

      maxSum = Math.max(maxSum, nums[i]);

    }

    return maxSum;
};
```









