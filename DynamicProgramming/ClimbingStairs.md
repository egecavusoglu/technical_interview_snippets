# Climbing Stairs

## Amazon, Apple, Goldman Sachs, Adobe, Bloomberg

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

```js
/**
 * @param {number} n
 * @return {number}
 */
var climbStairs = function (n) {
  let uniqueWays = [0, 1, 2];
  let counter = 3;
  while (counter <= n) {
    uniqueWays[counter] = uniqueWays[counter - 2] + uniqueWays[counter - 1];
    counter++;
  }
  return uniqueWays[n];
};
```
