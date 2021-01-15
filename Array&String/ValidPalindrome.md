# Valid Palindrome

## Microsoft

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.

Note: For the purpose of this problem, we define empty string as valid palindrome.

```
Input: "A man, a plan, a canal: Panama"
Output: true
```

```js
/**
 * @param {string} s
 * @return {boolean}
 */
var isPalindrome = function (s) {
  let cleanS = "";

  for (let i = 0; i < s.length; i++) {
    const c = s[i].toUpperCase();
    if (
      (c.charCodeAt(0) >= 65 && c.charCodeAt(0) <= 90) ||
      (c.charCodeAt(0) >= 48 && c.charCodeAt(0) <= 57)
    ) {
      cleanS += c;
    }
  }

  if (cleanS.length <= 1) return true;
  for (let i = 0; i < cleanS.length / 2; i++) {
    if (cleanS[i] !== cleanS[cleanS.length - i - 1]) return false;
  }
  return true;
};
```
