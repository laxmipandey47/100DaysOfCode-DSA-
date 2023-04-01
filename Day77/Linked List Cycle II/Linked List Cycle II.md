# 142. Linked List Cycle II

Given the `head` of a linked list, return the node where the cycle begins. If there is no cycle, return `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the next pointer. Internally, `pos` is used to denote the index of the node that tail's next pointer is connected to **(0-indexed)**. It is `-1` if there is no cycle. Note that `pos` **is not passed as a parameter**.

**Do not modify the linked list.**

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist.png" alt="img" style="height: 150px; width: 500px;"/>

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test2.png" alt="img" style="height: 150px; width: 200px;"/>

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```
**Example 3:**

<img src="https://assets.leetcode.com/uploads/2018/12/07/circularlinkedlist_test3.png" alt="img" style="height: 150px; width: 150px;"/>

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
``` 

**Constraints:**

* The number of the nodes in the list is in the range `[0, 104]`.
* `-105 <= Node.val <= 105`
* `pos` is `-1` or a **valid index** in the linked-list.

**Solution:**
```
public class Solution {
    public ListNode detectCycle(ListNode head) {
        if(head == null || head.next == null) {
            return null;
        }

        ListNode slow = head;
        ListNode fast = head;
        ListNode entry = head;

        while(fast.next != null && fast.next.next != null) {
            slow = slow.next; //Moving one node at a time
            fast = fast.next.next; // Moving two nodes at a time
            //If found the collision node of the two pointers
            if(slow == fast) {
                //Check for the entry point
                while(slow != entry) {
                    slow = slow.next;
                    entry = entry.next;
                }
                return entry;
            }
        }
        return null; 
    }
}
```
