# [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

Given a binary tree, you need to compute the length of the diameter of the tree. The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

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
var diameterOfBinaryTree = function(root) {

    let diameter = 0;

    const findDiameter = (node) => {
        if (!node) return 0;

        const left = findDiameter(node.left); // depth of left subtree
        const right = findDiameter(node.right); // depth of right subtree

        diameter = Math.max(diameter,  left + right); // update diameter if necessary

        return Math.max(left, right) + 1; // return depth rooted at `node` => depth of the bigger subtree + itself.
    }
    findDiameter(root);
    return diameter;
};
};
```
