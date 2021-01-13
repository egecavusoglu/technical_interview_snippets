# Sort Colors

## Microsoft

Given an array nums with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

Here, we will use the integers 0, 1, and 2 to represent the color red, white, and blue respectively.

Follow up:

Could you solve this problem without using the library's sort function?
Could you come up with a one-pass algorithm using only O(1) constant space?

```
Input: nums = [2,0,2,1,1,0]
Output: [0,0,1,1,2,2]
```

```js
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var sortColors = function (nums) {
  // Insert 0's to beginning of the array
  // Leave 1's
  // Move 2's to the end of the array.
  let i = 0;
  let length = nums.length;
  while (i < length) {
    let val = nums[i];
    if (val === 0) {
      nums.splice(i, 1);
      nums.unshift(val);
      i++;
    } else if (val === 1) {
      i++;
    } else if (val === 2) {
      nums.splice(i, 1);
      nums.push(val);
      length--; // !! IMPORTANT
    }
  }
};
```
