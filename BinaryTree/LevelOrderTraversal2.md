# Binary Tree Level Order Traversal II

Given a binary tree, return the bottom-up level order traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).

```
   3
   / \
  9  20
    /  \
   15   7

[
  [15,7],
  [9,20],
  [3]
]
```

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
let results = [];
var levelOrderBottom = function (root) {
  if (!root) return [];
  root.level = 0;
  traverse(root);
  const ret = results.reverse();
  results = [];
  return ret;
};

const traverse = (root) => {
  results[root.level]
    ? results[root.level].push(root.val)
    : (results[root.level] = [root.val]);
  if (root.left) {
    root.left.level = root.level + 1;
    traverse(root.left);
  }
  if (root.right) {
    root.right.level = root.level + 1;
    traverse(root.right);
  }
};
```
