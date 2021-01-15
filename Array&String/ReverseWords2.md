# Reverse Words in a String II

## Microsoft

Given an input string , reverse the string word by word.

```
Input:  ["t","h","e"," ","s","k","y"," ","i","s"," ","b","l","u","e"]
Output: ["b","l","u","e"," ","i","s"," ","s","k","y"," ","t","h","e"]
```

```js
/**
 * @param {character[]} s
 * @return {void} Do not return anything, modify s in-place instead.
 */
var reverseWords = function (s) {
  s.join("")
    .split(" ")
    .reverse()
    .join(" ")
    .split("")
    .forEach((c, index) => (s[index] = c));
};
```
