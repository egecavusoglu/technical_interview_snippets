# Merge Two Sorted Lists

Merge two sorted linked lists and return it as a sorted list. The list should be made by splicing together the nodes of the first two lists.

```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var mergeTwoLists = function (l1, l2) {
  let final = new ListNode(-1);
  let pointer = final;
  while (l1 || l2) {
    if (l1 && l2) {
      if (l1.val <= l2.val) {
        final.next = l1;
        l1 = l1.next;
      } else {
        final.next = l2;
        l2 = l2.next;
      }
    } else if (!l1) {
      final.next = l2;
      l2 = l2.next;
    } else if (!l2) {
      final.next = l1;
      l1 = l1.next;
    }
    final = final.next;
  }
  return pointer.next;
};
```
