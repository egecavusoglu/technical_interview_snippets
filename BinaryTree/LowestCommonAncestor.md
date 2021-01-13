Given a binary search tree (BST), find the lowest common ancestor (LCA) of two given nodes in the BST.

According to the definition of LCA on Wikipedia: “The lowest common ancestor is defined between two nodes p and q as the lowest node in T that has both p and q as descendants (where we allow a node to be a descendant of itself).”

![Image](./images/bst1.png)

Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8

Output: 6

Explanation: The LCA of nodes 2 and 8 is 6.

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */

/**
 * @param {TreeNode} root
 * @param {TreeNode} p
 * @param {TreeNode} q
 * @return {TreeNode}
 */
var lowestCommonAncestor = function (root, p, q) {
  let minNode = p.val < q.val ? p : q;
  let maxNode = p.val < q.val ? q : p;

  if (root.val == minNode.val || root.val == maxNode.val) {
    return root;
  }

  if (minNode.val < root.val && maxNode.val > root.val) {
    return root;
  }
  if (minNode.val < root.val) {
    return lowestCommonAncestor(root.left, minNode, maxNode);
  }
  if (minNode.val > root.val) {
    return lowestCommonAncestor(root.right, minNode, maxNode);
  }
};
```
