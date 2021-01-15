# Longest Palindromic Substring

## Microsoft

Given a string s, return the longest palindromic substring in s.

```
Input: s = "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```

```js
/**
 * @param {string} s
 * @return {string}
 */
// CASES:
// - cac -> [0,1], [0,2], [1,2]
// - caac -> we have to check 2n-1 [0,1], [1,1]
// - cadac -> we have to check 2(n-1) - 1 [0,1], [0,2], [1,2], [1,3], [2,3]

var longestPalindrome = function (s) {
  let length = s.length;
  let l = 0;
  let r = 0;
  let pos = [l, r];
  let maxLen = 0;
  for (let i = 0; i <= 2 * length - 3; i++) {
    const newPos = expand(s, l, r);
    const newLen = newPos[1] - newPos[0] + 1;
    if (newLen > maxLen) {
      pos = newPos;
      maxLen = newLen;
    }
    i % 2 === 0 ? r++ : l++;
  }

  return s.substring(pos[0], pos[1] + 1);
};

const expand = (s, l, r) => {
  if (l > r || s == null) return 0;
  while (s[l] && s[r] && s[l] == s[r]) {
    l--;
    r++;
  }
  l = l < 0 ? 0 : l + 1;
  r = r >= s.length ? s.length - 1 : r - 1;
  return [l, r];
};
```
