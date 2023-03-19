# 54. Spiral Matrix

Given an `m x n` `matrix`, return all elements of the `matrix` in spiral order.


**Example 1:**

<img src="https://assets.leetcode.com/uploads/2020/11/13/spiral1.jpg" alt="img" style="height: 100px; width: 100px;">

```
Input: matrix = [[1,2,3],[4,5,6],[7,8,9]]
Output: [1,2,3,6,9,8,7,4,5]
```
**Example 2:**

<img src="https://assets.leetcode.com/uploads/2020/11/13/spiral.jpg" alt="img" style="height: 100px; width: 100px;">


```
Input: matrix = [[1,2,3,4],[5,6,7,8],[9,10,11,12]]
Output: [1,2,3,4,8,12,11,10,9,5,6,7]
``` 

**Constraints:**

* `m == matrix.length`
* `n == matrix[i].length`
* `1 <= m, n <= 10`
* `-100 <= matrix[i][j] <= 100`

**Solution:**  
```
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ans = new ArrayList<>();
        int m = matrix.length;
        int n = matrix[0].length;
        int left = 0;
        int right = n - 1;
        int top = 0;
        int bottom = m - 1;

        while(m*n > ans.size()) {
            //for adding elements to the rightmost corner
            for(int i = left; i <= right; i++) {
                ans.add(matrix[top][i]);
            }

            //for adding elements till the last bottom element
            for(int i = top + 1; i <= bottom; i++) {
                ans.add(matrix[i][right]);
            }

            //avoiding multiple visit to same elemnt
            if(top != bottom) {
                //for adding all the left-most element
                for(int i = right - 1; i >= left; i--) {
                    ans.add(matrix[bottom][i]);
                }
            }

            if(left != right) {
                //for adding elements till the last top element
                for(int i = bottom - 1; i > top; i--) {
                    ans.add(matrix[i][left]);
                }
            }

            top++;
            bottom--;
            left++;
            right--;
        }
        return ans;
    }
}
```
