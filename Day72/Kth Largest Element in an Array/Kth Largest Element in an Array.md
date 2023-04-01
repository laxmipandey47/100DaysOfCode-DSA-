# 215. Kth Largest Element in an Array

Given an integer array `nums` and an integer `k`, return the `kth` largest element in the array.

Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

You must solve it in `O(n)` time complexity.

**Example 1:**
```
Input: nums = [3,2,1,5,6,4], k = 2
Output: 5
```
**Example 2:**
```
Input: nums = [3,2,3,1,2,4,5,5,6], k = 4
Output: 4
``` 

**Constraints:**

* `1 <= k <= nums.length <= 105`
* `-104 <= nums[i] <= 104`

**Solution:**
```
class Solution {
    public int findKthLargest(int[] nums, int k) {
        int ans;
        sort(nums, 0, nums.length - 1);
        ans = nums[nums.length - k];
        return ans;
    }

    public void sort(int[] nums, int low, int high){
         if(low >= high) {
          return;
         } 

         int s = low;
         int e = high;
         int m = s + (e - s)/2;
         int pivot = nums[m];
         while(s <= e) {
          //also a reason why if its already sorted it will not swap
          while(nums[s] < pivot) {
               s++;
          }

          while(nums[e] > pivot) {
               e--;
          }

          //swap
          if(s <= e) {
               int temp = nums[s];
               nums[s] = nums[e];
               nums[e] = temp;
               s++;
               e--;
          }
         }

         //recursion call
         //now my pivot is at correct index, 
         //sort the remaining two halves
         sort(nums, low, e);
         sort(nums, s, high);
     }
}
```
