# 106. Construct Binary Tree from Inorder and Postorder Traversal

Given two integer arrays `inorder` and `postorder` where `inorder` is the inorder traversal of a binary tree and `postorder` is the postorder traversal of the same tree, construct and return the binary tree.

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/02/19/tree.jpg" alt="img" style="height: 200px; width: 200px;"/>

```
Input: inorder = [9,3,15,20,7], postorder = [9,15,7,20,3]
Output: [3,9,20,null,null,15,7]
```
**Example 2:**

```
Input: inorder = [-1], postorder = [-1]
Output: [-1]
``` 

**Constraints:**

* `1 <= inorder.length <= 3000`
* `postorder.length == inorder.length`
* `-3000 <= inorder[i], postorder[i] <= 3000`
* `inorder` and `postorder` consist of **unique** values.
* Each value of `postorder` also appears in `inorder`.
* `inorder` is **guaranteed** to be the inorder traversal of the tree.
* `postorder` is **guaranteed** to be the postorder traversal of the tree.

**Solution:**
```
class Solution {
    public TreeNode buildTree(int[] inorder, int[] postorder) {
        return build(postorder, postorder.length - 1, inorder, 0, inorder.length -1);
    }

    private TreeNode build(int[] postorder, int posIdx, int[] inorder, int inStart, int inEnd) {
        if(inStart > inEnd || posIdx < 0) return null;
        TreeNode root = new TreeNode(postorder[posIdx]);
        int i = 0;
        for(i = inStart; i <= inEnd; i ++){
            if(inorder[i] == postorder[posIdx]) break;
        }

        root.right = build(postorder, posIdx - 1, inorder, i + 1, inEnd); 
        root.left = build(postorder, posIdx - 1 - (inEnd - i), inorder, inStart, i - 1);
        return root;
    }
}
```
