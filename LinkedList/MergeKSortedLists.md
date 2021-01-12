# Merge k Sorted Lists

## Microsoft

You are given an array of k linked-lists lists, each linked-list is sorted in ascending order.

Merge all the linked-lists into one sorted linked-list and return it.

Example 1:

Input: lists = [[1,4,5],[1,3,4],[2,6]]

Output: [1,1,2,3,4,4,5,6]

Explanation: The linked-lists are:

[1->4->5,1->3->4,2->6]

merging them into one sorted list:
1->1->2->3->4->4->5->6
Example 2:

Input: lists = []
Output: []
Example 3:

Input: lists = [[]]
Output: []

```js
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode[]} lists
 * @return {ListNode}
 */
var mergeKLists = function (lists) {
  if (lists.length === 0) return null;
  let resultList = lists[0];
  for (let i = 1; i < lists.length; i++) {
    resultList = mergeTwoLists(resultList, lists[i]);
  }
  return resultList;
};

const mergeTwoLists = (l1, l2) => {
  let resultList = new ListNode(-1);
  let currentNode = resultList;
  while (l1 || l2) {
    if (!l1) {
      currentNode.next = l2;
      currentNode = l2;
      l2 = l2.next;
    } else if (!l2) {
      currentNode.next = l1;
      currentNode = l1;
      l1 = l1.next;
    } else {
      if (l1.val <= l2.val) {
        currentNode.next = l1;
        currentNode = l1;
        l1 = l1.next;
      } else {
        currentNode.next = l2;
        currentNode = l2;
        l2 = l2.next;
      }
    }
  }
  return resultList.next;
};
```
