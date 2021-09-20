# #111

[Question here](https://leetcode.com/problems/minimum-depth-of-binary-tree/)

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
 * @return {number}
 */

function isLeaf(node) {
  return !node.left && !node.right;
}

var minDepth = function (root) {
  let minLength = Infinity;

  function traverse(node) {
    const currentLevel = node.level;
    if (isLeaf(node)) {
      minLength = Math.min(minLength, currentLevel);
    }
    if (node.left) {
      node.left.level = currentLevel + 1;
      traverse(node.left);
    }
    if (node.right) {
      node.right.level = currentLevel + 1;
      traverse(node.right);
    }
  }

  if (!root) return 0;
  root.level = 1;
  traverse(root);
  return minLength;
};
```
