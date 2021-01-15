# Reverse String

## Microsoft

Write a function that reverses a string. The input string is given as an array of characters char[].

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

You may assume all the characters consist of printable ascii characters.

```
Input: ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

```js
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseString = function (s) {
  for (let i = 0; i < s.length / 2; i++) {
    let temp = s[i];
    s[i] = s[s.length - (i + 1)];
    s[s.length - (i + 1)] = temp;
  }
  return s;
};
```
