# [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/)

Given a binary tree

```
struct Node {
  int val;
  Node *left;
  Node *right;
  Node *next;
}
```

Populate each next pointer to point to its next right node. If there is no next right node, the next pointer should be set to NULL.

Initially, all next pointers are set to NULL.

![BST Tree 2](./images/bs2.png)

```
Input: root = [1,2,3,4,5,null,7]
Output: [1,#,2,3,#,4,5,7,#]
Explanation: Given the above binary tree (Figure A), your function should populate each next pointer to point to its next right node, just like in Figure B. The serialized output is in level order as connected by the next pointers, with '#' signifying the end of each level.
```

```js
/**
 * // Definition for a Node.
 * function Node(val, left, right, next) {
 *    this.val = val === undefined ? null : val;
 *    this.left = left === undefined ? null : left;
 *    this.right = right === undefined ? null : right;
 *    this.next = next === undefined ? null : next;
 * };
 */

/**
 * @param {Node} root
 * @return {Node}
 */
var connect = function (root) {
  if (!root) return root;
  root.level = 0;
  let levels = [];
  traverse(root, levels);

  levels.forEach((level) => {
    for (let i = 0; i < level.length - 1; i++) {
      level[i].next = level[i + 1];
    }
  });
  return root;
};

const traverse = (root, levels) => {
  if (root.left) {
    root.left.level = root.level + 1;

    levels[root.left.level]
      ? levels[root.left.level].push(root.left)
      : (levels[root.left.level] = [root.left]);
    traverse(root.left, levels);
  }
  if (root.right) {
    root.right.level = root.level + 1;
    levels[root.right.level]
      ? levels[root.right.level].push(root.right)
      : (levels[root.right.level] = [root.right]);
    traverse(root.right, levels);
  }
};
```

## A better solution by Leetcode.

```js
var connect = function (root) {
  let parent = root;
  while (parent) {
    let dummy = new Node();
    let curr = dummy;
    while (parent) {
      if (parent.left) {
        curr.next = parent.left;
        curr = curr.next;
      }
      if (parent.right) {
        curr.next = parent.right;
        curr = curr.next;
      }
      parent = parent.next;
    }
    parent = dummy.next;
  }
  return root;
};
```
