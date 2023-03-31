# 104. Maximum Depth of Binary Tree

Given the `root` of a binary tree, return its maximum depth.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2020/11/26/tmp-tree.jpg" alt="img" style="height:200px; width: 200px;"/>

Input: root = [3,9,20,null,null,15,7]
Output: 3
**Example 2:**
```
Input: root = [1,null,2]
Output: 2
```
**Constraints:**

* The number of nodes in the tree is in the range `[0, 104]`.
* `-100 <= Node.val <= 100`

**Solution:**
```
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) {
            return 0;
        }

        int leftHeight = maxDepth(root.left);
        int rightHeight = maxDepth(root.right);

        return 1 + Math.max(leftHeight, rightHeight);
    }
}
```
