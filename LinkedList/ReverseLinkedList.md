# Reverse Linked List

## Microsoft

Reverse a singly linked list.

Example:

Input: 1->2->3->4->5->NULL

Output: 5->4->3->2->1->NULL

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */

var reverseList = function (head) {
  if (!head) return head;
  if (!head.next) return head;
  let prevNode = head;
  let currentNode = head.next ? head.next : head;
  prevNode.next = null;
  let nextNode;

  while (currentNode) {
    nextNode = currentNode.next;

    currentNode.next = prevNode;
    // console.log(currentNode)
    prevNode = currentNode;
    currentNode = nextNode;
  }
  return prevNode;
};
```
