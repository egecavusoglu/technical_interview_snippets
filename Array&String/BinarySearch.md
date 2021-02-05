# Binary Search

Given a sorted (in ascending order) integer array nums of n elements and a target value, write a function to search target in nums. If target exists, then return its index, otherwise return -1.

```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
var search = function (nums, target) {
  // return nums.indexOf(target)
  let left = 0,
    right = nums.length - 1;
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    const val = nums[mid];
    if (val == target) {
      return mid;
    } else if (val < target) {
      // in the left subarray
      left = mid + 1;
    } else {
      right = mid - 1;
    }
  }
  return -1;
};
```
