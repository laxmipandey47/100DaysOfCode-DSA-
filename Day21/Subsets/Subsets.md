# 78. Subsets

Given an integer array nums of `unique` elements, return all possible 
subsets
 (the power set).

The solution set `must not` contain duplicate subsets. Return the solution in `any order`.

**Example 1:**
```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```
**Example 2:**
```
Input: nums = [0]
Output: [[],[0]]
``` 

**Constraints:**

* `1 <= nums.length <= 10`
* `-10 <= nums[i] <= 10`
* All the numbers of nums are unique.

**Solution:** 
```
class Solution {
    public List<List<Integer>> subsets(int[] nums) {
        int length = nums.length;
        //range of the numbers
        //or pow(2, n) is same as (1 << n)
        int n = (1 << length) - 1; 

        List<List<Integer>> ans = new ArrayList<>();
        ans.add(new ArrayList<Integer>());

        //get subsets using bit manipulation
        while(n > 0) {
            int temp = n;
            int i = length - 1;

            List<Integer> result = new ArrayList<>();
            while(temp > 0) {
                //check for the set bit -> 1
                if((temp & 1) > 0)  {
                    result.add(nums[i]);
                }
                temp = temp >> 1;
                i -= 1;
            }
            ans.add(result);
            n -= 1;
        }

        return ans;
    }
    
}
```
