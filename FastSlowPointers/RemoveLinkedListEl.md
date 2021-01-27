# Remove Linked List Elements

```
Input:  1->2->6->3->4->5->6, val = 6
Output: 1->2->3->4->5
```

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
 * @param {number} val
 * @return {ListNode}
 */
var removeElements = function (head, val) {
  let origin = head;
  let prev = null;
  while (head) {
    if (head.val === val) {
      // Remove node
      if (prev) {
        prev.next = head.next;
      } else {
        origin = head.next;
      }
    } else {
      prev = head;
    }
    head = head.next;
  }
  return origin;
};
```
