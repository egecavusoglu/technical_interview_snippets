# Best Time to Buy and Sell Stock

## Microsoft

You are given an array prices for which prices[i] is the price of a given stock on the ith day.

You are only permitted to complete at most one transaction. In other words, you can buy one and sell one share of the stock. You cannot sell a stock before you buy one.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
The answer is not 7-1 = 6, as selling price needs to be larger than buying price.
```

```js
/**
 * @param {number[]} prices
 * @return {number}
 */
var maxProfit = function (prices) {
  let left = 0;
  let right = 1;
  let maxProfit = 0;
  let i = 0;
  while (right < prices.length) {
    let profit = prices[right] - prices[left];
    if (profit < 0) {
      left = right;
      right++;
    } else if (profit >= 0) {
      maxProfit = profit > maxProfit ? profit : maxProfit;
      right++;
    }

    i++;
  }
  return maxProfit;
};
```
