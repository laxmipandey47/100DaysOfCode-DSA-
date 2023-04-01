# 382. Linked List Random Node

Given a singly linked list, return a random node's value from the linked list. Each node must have the **same probability** of being chosen.

Implement the `Solution` class:

* `Solution(ListNode head)` Initializes the object with the head of the singly-linked list `head`.
* `int getRandom()` Chooses a node randomly from the list and returns its value. All the nodes of the list should be equally likely to be chosen.
 
**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/03/16/getrand-linked-list.jpg" alt="img" style="height: 100px; width: 300px;"/>

```
Input
["Solution", "getRandom", "getRandom", "getRandom", "getRandom", "getRandom"]
[[[1, 2, 3]], [], [], [], [], []]
Output
[null, 1, 3, 2, 2, 3]

Explanation
Solution solution = new Solution([1, 2, 3]);
solution.getRandom(); // return 1
solution.getRandom(); // return 3
solution.getRandom(); // return 2
solution.getRandom(); // return 2
solution.getRandom(); // return 3
// getRandom() should return either 1, 2, or 3 randomly. Each element should have equal probability of returning.
``` 

**Constraints:**

* The number of nodes in the linked list will be in the range `[1, 104]`.
* `-104 <= Node.val <= 104`
* At most 104 calls will be made to `getRandom`.

**Solution:**
```
class Solution {

    private Random rand;
    private ListNode head;
    
    /** @param head The linked list's head.
        Note that the head is guaranteed to be not null, so it contains at least one node. */
    public Solution(ListNode head) {
        this.head = head;
        rand = new Random();
    }

    /** Returns a random node's value. */
    public int getRandom() {
        int result = -1;
        ListNode p = head;
        int count = 0;

        while (p != null) {
            count++;
            if (rand.nextInt(count) < 1) {
                result = p.val;
            }
            p = p.next;
        }
        return result;
    }
}
```
