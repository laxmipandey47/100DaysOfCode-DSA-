# 912. Sort an Array

Given an array of integers `nums`, sort the array in ascending order and return it.

You must solve the problem **without using any built-in functions** in `O(nlog(n))` time complexity and with the smallest space complexity possible.

**Example 1:**
```
Input: nums = [5,2,3,1]
Output: [1,2,3,5]
Explanation: After sorting the array, the positions of some numbers are not changed (for example, 2 and 3), 
while the positions of other numbers are changed (for example, 1 and 5).
```
**Example 2:**
```
Input: nums = [5,1,1,2,0,0]
Output: [0,0,1,1,2,5]
Explanation: Note that the values of nums are not necessairly unique.
``` 

**Constraints:**

* `1 <= nums.length <= 5 * 104`
* `-5 * 104 <= nums[i] <= 5 * 104`

**Solution:**
```
class Solution {
    public int[] sortArray(int[] nums) {
        //Quick Sort
        sort(nums, 0, nums.length - 1);

        return nums;
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
         //now my pivot is at correct index, please sort two halves
         sort(nums, low, e);
         sort(nums, s, high);
     }
}
```
