# Missing Number

### Amazon, Capital One, Microsoft, Facebook, Apple

Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

Follow up: Could you implement a solution using only O(1) extra space complexity and O(n) runtime complexity?

```
Input: nums = [3,0,1]
Output: 2
Explanation: n = 3 since there are 3 numbers, so all numbers are in the range [0,3]. 2 is the missing number in the range since it does not appear in nums.
```

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var missingNumber = function (nums) {
  // 1 + 2 + ... + n = n(n+1) / 2;
  const n = nums.length;
  let expectedSum = (n * (n + 1)) / 2;
  let sum = 0;
  nums.forEach((num) => (sum += num));
  return expectedSum - sum;
};
```
