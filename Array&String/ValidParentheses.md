# Valid Parentheses

## Microsoft

Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.

```
Input: s = "()[]{}"
Output: true
```

```js
/**
 * @param {string} s
 * @return {boolean}
 */

const dic = {
  "(": ")",
  "{": "}",
  "[": "]",
};

var isValid = function (s) {
  if (s.length % 2 != 0) return false;
  let pairs = 0;
  let stack = [];
  for (let i = 0; i < s.length; i++) {
    if (s[i] == "(" || s[i] == "{" || s[i] == "[") {
      // console.log("PUSHING", s[i])
      stack.push(s[i]);
    } else {
      const el = stack.pop();
      if (dic[el] != s[i]) {
        return false;
      }
      pairs++;
    }
  }

  if (pairs != s.length / 2) return false;

  return true;
};
```
