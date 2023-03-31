# 103. Binary Tree Zigzag Level Order Traversal

Given the `root` of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).

**Example 1:**

<img src="https://assets.leetcode.com/uploads/2021/02/19/tree1.jpg" alt="img" style="height: 200px; width: 200px;"/>

```
Input: root = [3,9,20,null,null,15,7]
Output: [[3],[20,9],[15,7]]
```
**Example 2:**
```
Input: root = [1]
Output: [[1]]
```
**Example 3:**
```
Input: root = []
Output: []
``` 

**Constraints:**

* The number of nodes in the tree is in the range `[0, 2000]`.
* `-100 <= Node.val <= 100`

**Solution:**
```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        if(root == null) {
            return new ArrayList<>();
        }

        List<List<Integer>> ans = new ArrayList<>();
        Queue<TreeNode> q = new LinkedList();
        q.add(root);

        boolean reverseDir = false;

        while(!q.isEmpty()) {
            int size = q.size();
            List<Integer> level = new ArrayList<>();
            while(size-- > 0) {
                root = q.poll();
                level.add(root.val);
                if(root.left != null) 
                q.add(root.left);
                if(root.right != null) 
                q.add(root.right);

            }
            if(reverseDir) {
                Collections.reverse(level);
            }
            ans.add(level);
            reverseDir = !reverseDir;
        }
        return ans;
    }
}
```
