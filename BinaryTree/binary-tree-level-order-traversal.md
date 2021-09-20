# #102

[Question here](https://leetcode.com/problems/binary-tree-level-order-traversal/)

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
 * @return {number[][]}
 */
var levelOrder = function (root) {
  const orders = [];
  function traverse(node) {
    orders[node.level]
      ? orders[node.level].push(node.val)
      : (orders[node.level] = [node.val]);

    const currentLevel = node.level;

    if (node.left) {
      node.left.level = currentLevel + 1;
      traverse(node.left);
    }
    if (node.right) {
      node.right.level = currentLevel + 1;
      traverse(node.right);
    }
  }

  if (!root) return [];

  root.level = 0;
  traverse(root);

  return orders;
};
```
