# 109. Convert Sorted List to Binary Search Tree

Given the `head` of a singly linked list where elements are sorted in **ascending order**, convert it to a height-balanced binary search tree.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2020/08/17/linked.jpg" alt="img" style="height: 300px; width: 500px;"/>

```
Input: head = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: One possible answer is [0,-3,9,-10,null,5], which represents the shown height balanced BST.
```
**Example 2:**

```
Input: head = []
Output: []
``` 

**Constraints:**

* The number of nodes in `head` is in the range `[0, 2 * 104]`.
* `-105 <= Node.val <= 105`

**Solution:**
```
class Solution {
  public TreeNode sortedListToBST(ListNode head) {
    if (head == null)
      return null;
    if (head.next == null)
      return new TreeNode(head.val);

    ListNode mid = findMid(head);
    TreeNode root = new TreeNode(mid.val);
    root.left = sortedListToBST(head);
    root.right = sortedListToBST(mid.next);

    return root;
  }

  private ListNode findMid(ListNode head) {
    ListNode prev = null;
    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {
      prev = slow;
      slow = slow.next;
      fast = fast.next.next;
    }
    prev.next = null;

    return slow;
  }
}
```
