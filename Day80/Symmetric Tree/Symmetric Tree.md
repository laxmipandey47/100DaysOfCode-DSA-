# 101. Symmetric Tree

Given the `root` of a binary tree, check whether it is a mirror of itself (i.e., symmetric around its center).

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree1.jpg" alt="img" style="height: 200px; width: 400px;"/>

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2021/02/19/symtree2.jpg" alt="img" style="height: 200px; width: 400px;"/>

```
Input: root = [1,2,2,null,3,null,3]
Output: false
``` 

**Constraints:**

* The number of nodes in the tree is in the range [1, 1000].
* `-100 <= Node.val <= 100`

**Solution:**
```
class Solution {
    private boolean check(TreeNode root1,TreeNode root2){
        if(root1==null || root2==null){
            return root1==root2;
        }
        return root1.val==root2.val && check(root1.left,root2.right) && check(root1.right,root2.left);
    }
    public boolean isSymmetric(TreeNode root) {
        return check(root,root);
    }
}
```
