# Rotate Image

You are given an n x n 2D matrix representing an image, rotate the image by 90 degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. DO NOT allocate another 2D matrix and do the rotation.

![Example Image](./images/as2.jpg)

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [[7,4,1],[8,5,2],[9,6,3]]
```

```js
/**
 * @param {number[][]} matrix
 * @return {void} Do not return anything, modify matrix in-place instead.
 */
var rotate = function (matrix) {
  // First transpose
  // Then mirror
  return mirror(transpose(matrix));
};

const transpose = (matrix) => {
  for (let i = 0; i < matrix.length; i++) {
    for (let j = i; j < matrix[0].length; j++) {
      [matrix[i][j], matrix[j][i]] = [matrix[j][i], matrix[i][j]];
    }
  }
  return matrix;
};

const mirror = (matrix) => {
  const width = matrix[0].length;
  for (let i = 0; i < matrix.length; i++) {
    for (let j = 0; j < width / 2; j++) {
      [matrix[i][j], matrix[i][width - j - 1]] = [
        matrix[i][width - j - 1],
        matrix[i][j],
      ];
    }
  }
  return matrix;
};
```
