# 238. Product of Array Except Self

Given an integer array `nums`, return an array `answer` such that `answer[i]` is equal to the product of all the elements of `nums` except `nums[i]`.

The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Example 1:**
```
Input: nums = [1,2,3,4]
Output: [24,12,8,6]
```
**Example 2:**
```
Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]
``` 

**Constraints:**

* `2 <= nums.length <= 105`
* `-30 <= nums[i] <= 30`
* The product of any prefix or suffix of `nums` is guaranteed to fit in a 32-bit integer

**Solution:**
```
class Solution {
    public int[] productExceptSelf(int[] nums) {
        //Approach: Creating two arrays one for storing the right product of the array elements 
        //and ans array for storing the product of array element except the i(th) element 
        //by multiplying right array with a product variable for storing the last obtained product
        //returning the resulting array

        int[] right = new int[nums.length];
        int leftProd = 1;
        for(int i = nums.length - 1; i >= 0; i--) {
            leftProd *= nums[i];
            right[i] = leftProd;
        }

        leftProd = 1;
        int[] ans = new int[nums.length];
        for(int i = 0; i < nums.length - 1; i++) {
            int lp = leftProd;
            int rp = right[i + 1];

            ans[i] = lp*rp;
            leftProd *= nums[i];
        }

        ans[nums.length - 1] = leftProd;

        return ans;
    }
}
```
