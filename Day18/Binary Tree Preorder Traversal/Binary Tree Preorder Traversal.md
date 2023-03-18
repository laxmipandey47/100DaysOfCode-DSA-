# 144. Binary Tree Preorder Traversal

Given the root of a binary tree, return the preorder traversal of its nodes' values.

**Example 1:**<br>

![img](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)
```
Input: root = [1,null,2,3]
Output: [1,2,3]
```
**Example 2:**
```
Input: root = []
Output: []
```
**Example 3:**
```
Input: root = [1]
Output: [1]
```

**Constraints:**

* The number of nodes in the tree is in the range `[0, 100]`.
* ```-100 <= Node.val <= 100```

**Solution:** 
```
class Solution {
    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> list = new ArrayList<>();
        return preOrder(root, list);
    }

    //recursive function to get preorder list
    public List<Integer> preOrder(TreeNode root, List<Integer> list) {
        if(root == null) {
            return list;
        }

        //add in preorder
        list.add(root.val);

        preOrder(root.left, list);
        preOrder(root.right, list);

        return list;
    }
}
```
