# 783. Minimum Distance Between BST Nodes

Given the `root` of a Binary Search Tree (BST), return the minimum difference between the values of any two different nodes in the tree.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/02/05/bst1.jpg" alt="" style="height: 200px; width: 200px;"/>

```
Input: root = [4,2,6,1,3]
Output: 1
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2021/02/05/bst2.jpg" alt="" style="height: 200px; width: 200px;"/>

```
Input: root = [1,0,48,null,null,12,49]
Output: 1
``` 

**Constraints:**

* The number of nodes in the tree is in the range `[2, 100]`.
* `0 <= Node.val <= 105`

**Solution:**
```
class Solution {
    public int minDiffInBST(TreeNode root) {
        int[] minDiff = {Integer.MAX_VALUE};
        Integer[] prevVal = {null};
        inorder(root, minDiff, prevVal);
        return minDiff[0];
    }
    
    private void inorder(TreeNode node, int[] minDiff, Integer[] prevValue) {
        if (node == null) {
            return;
        }
        inorder(node.left, minDiff, prevValue);
        if (prevValue[0] != null) {
            minDiff[0] = Math.min(minDiff[0], node.val - prevValue[0]);
        }
        prevValue[0] = node.val;
        inorder(node.right, minDiff, prevValue);
    }
}
```
