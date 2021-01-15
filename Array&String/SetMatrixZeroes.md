# Set Matrix Zeroes

## Microsoft

Given an m x n matrix. If an element is 0, set its entire row and column to 0. Do it in-place.

Follow up:

A straight forward solution using O(mn) space is probably a bad idea.
A simple improvement uses O(m + n) space, but still not the best solution.
Could you devise a constant space solution?

![Image](./images/mat1.jpg)

```
Input: matrix = [[1,1,1],[1,0,1],[1,1,1]]
Output: [[1,0,1],[0,0,0],[1,0,1]]
```

```js
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var setZeroes = function (matrix) {
  const rows = [];
  const cols = [];
  const w = matrix[0].length;
  const h = matrix.length;
  for (let i = 0; i < h; i++) {
    for (let j = 0; j < w; j++) {
      if (matrix[i][j] === 0) {
        cols.push(j);
        rows.push(i);
      }
    }
  }
  cols.forEach((c) => {
    for (let i = 0; i < h; i++) matrix[i][c] = 0;
  });
  rows.forEach((r) => {
    for (let i = 0; i < w; i++) matrix[r][i] = 0;
  });
  // console.log(matrix)
};
```
