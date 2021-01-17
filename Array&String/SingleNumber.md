# Single Number

### Facebook, Amazon, Bloomberg, Microsoft, Google, Adobe

Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

Follow up: Could you implement a solution with a linear runtime complexity and without using extra memory?

```
Input: nums = [4,1,2,1,2]
Output: 4
```

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  nums = nums.sort();
  for (let i = 0; i < nums.length; i += 2) {
    if (nums[i] != nums[i + 1]) return nums[i];
  }
};
```

## A faster and better but very trivial solution

```js
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function (nums) {
  return nums.reduce((acc, curr) => (acc ^= curr));
};
```
