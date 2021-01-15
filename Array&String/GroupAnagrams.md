# Group Anagrams

## Microsoft

Given an array of strings strs, group the anagrams together. You can return the answer in any order.

An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

```
Input: strs = ["eat","tea","tan","ate","nat","bat"]
Output: [["bat"],["nat","tan"],["ate","eat","tea"]]
```

```js
/**
 * @param {string[]} strs
 * @return {string[][]}
 */
var groupAnagrams = function (strs) {
  let dic = {};
  strs.forEach((str) => {
    const key = Array.from(str).sort().join("");
    if (key in dic) {
      dic[key].push(str);
    } else {
      dic[key] = [str];
    }
  });
  return Object.values(dic);
};
```
