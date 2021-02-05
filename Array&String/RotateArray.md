# [Rotate Array](https://leetcode.com/problems/rotate-array/)

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function (nums, k) {
  const copy = Array.from(nums);
  const length = nums.length;
  copy.map((item, ind) => {
    nums[(ind + k) % length] = item;
  });
};
```

Constant space solution

```js
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var rotate = function (nums, k) {
  if (nums.length == 1) {
    return nums;
  } else if (k > nums.length) {
    k -= nums.length;
  }
  nums.reverse();
  nReverse(nums, 0, k - 1);
  nReverse(nums, k, nums.length - 1);
};

function nReverse(array, start, end) {
  while (start < end) {
    var temp = array[start];
    array[start] = array[end];
    array[end] = temp;
    start++;
    end--;
  }
}
```
