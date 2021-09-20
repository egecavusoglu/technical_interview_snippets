# [Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var maxSubArray = function (nums) {
  let maxSum = nums[0];
  let sum = 0;
  for (let i = 0; i < nums.length; i++) {
    if (sum < 0) {
      sum = 0;
    }
    sum += nums[i];
    maxSum = Math.max(maxSum, sum);
  }
  return maxSum;
};
```
