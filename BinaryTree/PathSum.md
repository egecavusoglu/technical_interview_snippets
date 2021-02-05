# [Path Sum](https://leetcode.com/problems/path-sum/)

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} targetSum
 * @return {boolean}
 */

var hasPathSum = function (root, targetSum) {
  if (!root) return false;
  const traverse = (root) => {
    if (!root) return false;

    if (root.sum == targetSum && isLeaf(root)) {
      // res = true;
      return true;
    }
    root.left ? (root.left.sum = root.sum + root.left.val) : null;
    root.right ? (root.right.sum = root.sum + root.right.val) : null;

    return traverse(root.left, targetSum) || traverse(root.right, targetSum);
  };
  root.sum = root.val;
  const res = traverse(root, targetSum);
  return res;
};

const isLeaf = (node) => {
  if (!node.left && !node.right) {
    return true;
  }
  return false;
};
```
