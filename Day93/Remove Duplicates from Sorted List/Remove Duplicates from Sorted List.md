# 83. Remove Duplicates from Sorted List

Given the `head` of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list **sorted** as well.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/01/04/list1.jpg" alt="img" style="height: 200px; width: 250px;"/>

```
Input: head = [1,1,2]
Output: [1,2]
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2021/01/04/list2.jpg" alt="img" style="height: 200px; width: 400px;"/>

```
Input: head = [1,1,2,3,3]
Output: [1,2,3]
``` 

**Constraints:**

* The number of nodes in the list is in the range `[0, 300]`.
* `-100 <= Node.val <= 100`
* The list is guaranteed to be **sorted** in ascending order.

**Solution:**
```
class Solution {
    public ListNode deleteDuplicates(ListNode node) {
        if(node == null) {
          return node;
        }
        ListNode head = node;
        while(node.next != null) {
          if(node.val ==node.next.val) {
               node.next = node.next.next;
          }
          else {
               node = node.next;
          }
        }
        return head;
    }
}
```
