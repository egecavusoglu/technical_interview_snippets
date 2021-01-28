# Invert Binary Tree

Invert a binary tree.

```
FROM
     4
   /   \
  2     7
 / \   / \
1   3 6   9
```

```
TO
     4
   /   \
  7     2
 / \   / \
9   6 3   1
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
 * @return {TreeNode}
 */
var invertTree = function (root) {
  if (!root) return root;
  let temp = root.right;
  root.right = root.left;
  root.left = temp;
  root.right && invertTree(root.right);
  root.left && invertTree(root.left);
  return root;
};
```
