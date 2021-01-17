# Contains Duplicate

## Apple,

Given an array of integers, find if the array contains any duplicates.

Your function should return true if any value appears at least twice in the array, and it should return false if every element is distinct.

```
Input: [1,2,3,1]
Output: true
```

### Even better to use Sets

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function (nums) {
  return nums.length > new Set(nums).size;
};
```

```js
/**
 * @param {number[]} nums
 * @return {boolean}
 */
var containsDuplicate = function (nums) {
  let dic = {};
  for (let i = 0; i < nums.length; i++) {
    const n = nums[i];
    if (n in dic) {
      return true;
    } else {
      dic[n] = 1;
    }
  }
  return false;
};
```
