# Spiral Matrix

## Microsoft

Given an m x n matrix, return all elements of the matrix in spiral order.

![image](./images/as3.jpg)

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
```

```js
/**
 * @param {number[][]} matrix
 * @return {number[]}
 */
var spiralOrder = function (matrix) {
  const result = []; // Declare constant variable result initialzie to an empty array.

  let startRow = 0,
    endRow = matrix.length - 1;
  let startCol = 0,
    endCol = matrix[0].length - 1;

  while (startCol <= endCol && startRow <= endRow) {
    // top row
    for (let col = startCol; col <= endCol; col++) {
      result.push(matrix[startRow][col]);
    }
    // right row minus top column
    for (let row = startRow + 1; row <= endRow; row++) {
      result.push(matrix[row][endCol]);
    }
    // bottom row minus last column
    for (let col = endCol - 1; col >= startCol; col--) {
      if (startRow === endRow) break;
      result.push(matrix[endRow][col]);
    }
    // remaining cols
    for (let row = endRow - 1; row > startRow; row--) {
      if (startCol === endCol) break;
      result.push(matrix[row][startCol]);
    }
    startRow++;
    endRow--;
    startCol++;
    endCol--;
  }

  return result; // Return result
};
```
