# Double array:: O(N), O(N)



{% embed url="https://leetcode.com/problems/maximum-sum-circular-subarray/submissions/964943441/" %}
solution:: double arr
{% endembed %}

```javascript

var maxSubarraySumCircular = function(nums) {
    let nonCircularSubArraySum = -Infinity;

    let currSum = 0;
    for (let i = 0; i < nums.length; i++) {
        const curr = nums[i];
        currSum = Math.max(currSum + curr, curr);
        nonCircularSubArraySum = Math.max(currSum, nonCircularSubArraySum); 
    }

    // [7][5][5][5][5][7]
    // [5,-3,5][5,-3,5]
    const sums = new Array(nums.length * 2).fill(-Infinity);
    currSum = 0;
    for (let i = nums.length - 1; i >= 0; i--) {
        const curr = nums[i];
        currSum += curr;
        sums[i] = Math.max(currSum, sums[i + 1]);
    }
    currSum = nums[0];
    sums[nums.length] = nums[0];
    for (let i = 1; i < nums.length; i++) {
        const curr = nums[i];
        currSum += curr;
        sums[nums.length + i] = Math.max(sums[nums.length + i - 1], currSum);
    }

    // [-5,3,5][-5,3,5]
    // [8][8][5][-5][-2][3]
    let circularSubArraySum = -Infinity;
    for (let i = 1; i < nums.length; i++) {
        circularSubArraySum = Math.max(circularSubArraySum, sums[i] + sums[nums.length - 1 + i]);
    }

    return Math.max(nonCircularSubArraySum, circularSubArraySum);

};
```

