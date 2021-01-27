# Palindrome Linked List

Given a singly linked list, determine if it is a palindrome.

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
 * @return {boolean}
 */
var isPalindrome = function (head) {
  let slow = head;
  let fast = head;

  // Find the middle node.
  while (fast && fast.next) {
    slow = slow.next;
    fast = fast.next.next;
  }

  // Reverse the second half of the list.
  // []=>[]=>[]
  let prev = null;
  while (slow) {
    let temp = slow.next;
    slow.next = prev;
    prev = slow;
    slow = temp;
  }

  // Start comparing for palindrome
  // [head] => [] => [] <= [prev]
  while (prev) {
    if (head.val != prev.val) return false;
    head = head.next;
    prev = prev.next;
  }
  return true;
};
```
