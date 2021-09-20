# #637

[Question here](https://leetcode.com/problems/average-of-levels-in-binary-tree/submissions/)

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
 * @return {number[]}
 */
var averageOfLevels = function (root) {
  const avgMap = {};

  function traverse(node) {
    const currentLevel = node.level;
    if (currentLevel in avgMap) {
      avgMap[currentLevel].avg = avgMap[currentLevel].avg + node.val;
      avgMap[currentLevel].count = avgMap[currentLevel].count + 1;
    } else {
      avgMap[currentLevel] = {
        avg: node.val,
        count: 1,
      };
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

  if (!root) {
    return [];
  }
  root.level = 0;
  traverse(root);

  const results = [];
  Object.keys(avgMap).map((i) => {
    i = avgMap[i];
    results.push(i.avg / i.count);
  });
  return results;
};
```
