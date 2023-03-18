# 41. First Missing Positive

Given an unsorted integer array **nums**, return the smallest missing positive integer.

You must implement an algorithm that runs in **O(n)** time and uses constant extra space.

**Example 1:**
```
Input: nums = [1,2,0]
Output: 3
Explanation: The numbers in the range [1,2] are all in the array.
```

**Example 2:**
```
Input: nums = [3,4,-1,1]
Output: 2
Explanation: 1 is in the array but 2 is missing.
```

**Example 3:**
```
Input: nums = [7,8,9,11,12]
Output: 1
Explanation: The smallest positive integer 1 is missing.
```

**Constraints:**

* ```1 <= nums.length <= 105```
* ```-231 <= nums[i] <= 231 - 1```

**Solution: **
```
class Solution {
    public int firstMissingPositive(int[] nums) {
        int i = 0;
          while( i < nums.length) {
               int correct = nums[i] - 1;
               if(nums[i] > 0 && nums[i] < nums.length && nums[i] != nums[correct]) {
                    swapArray(nums, i, correct);
               }
               else {
                    i++;
               }
          }
          
          //search for first missing number
          for(int index = 0; index < nums.length; index++ ) {
               if(nums[index] != index + 1) {
                    return index + 1;
               }
          }

          //case 2
          return nums.length + 1;
     }

     void swapArray(int[] nums, int first, int second) {
          int temp = nums[first];
          nums[first] = nums[second];
          nums[second] = temp;
    }
}
```
