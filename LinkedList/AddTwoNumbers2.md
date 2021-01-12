# Add Two Numbers II

## Microsoft

You are given two non-empty linked lists representing two non-negative integers. The most significant digit comes first and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

Follow up:
What if you cannot modify the input lists? In other words, reversing the lists is not allowed.

Example:

Input: (7 -> 2 -> 4 -> 3) + (5 -> 6 -> 4)
Output: 7 -> 8 -> 0 -> 7

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
var addTwoNumbers = function (l1, l2) {
  l1 = reverseList(l1);
  l2 = reverseList(l2);
  return reverseList(addTwoNumbersRev(l1, l2));
};

var addTwoNumbersRev = function (l1, l2) {
  let carry = 0;
  let resultList = new ListNode(null, null);
  let currentNode = resultList;
  while (l1 || l2) {
    // Find the sum of digits
    const l1Val = l1?.val ? l1.val : 0;
    const l2Val = l2?.val ? l2.val : 0;
    let sum = l1Val + l2Val + carry;
    // Update carry
    carry = sum > 9 ? 1 : 0;
    sum = sum % 10;
    // Append the sum to the final list.
    const node = new ListNode(sum, null);
    currentNode.next = node;
    currentNode = node;
    // Update l1, l2
    l1 = l1?.next;
    l2 = l2?.next;
  }
  if (carry === 1) {
    currentNode.next = new ListNode(1, null);
  }
  resultList = resultList.next;
  return resultList;
};

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
