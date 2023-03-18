# 974. Subarray Sums Divisible by K

Given an integer array `nums` and an integer `k`, return the number of non-empty **subarrays** that have a sum divisible by `k`.

A **subarray** is a **contiguous** part of an array.

 
**Example 1:**
```
Input: nums = [4,5,0,-2,-3,1], k = 5
Output: 7
Explanation: There are 7 subarrays with a sum divisible by k = 5:
[4, 5, 0, -2, -3, 1], [5], [5, 0], [5, 0, -2, -3], [0], [0, -2, -3], [-2, -3]
```
**Example 2:**
```
Input: nums = [5], k = 9
Output: 0
```

**Constraints:**

* `1 <= nums.length <= 3 * 104`
* `-104 <= nums[i] <= 104`
* `2 <= k <= 104`

**Solution:** 
```
class Solution {
    public int subarraysDivByK(int[] nums, int k) {
        int ans = 0;

        //HashMap for storing frequency of the remainder
        HashMap<Integer, Integer> map = new HashMap<>();
        map.put(0, 1);
        int sum = 0;
        int rem = 0;

        for(int i = 0; i < nums.length; i++) {
            sum += nums[i];
            rem = sum % k;
            //if remainder is -ve add the given k value
            //since for example for -2 the remainder is -2
            //therefore, it will be -2 + 7 = 5
            if(rem < 0) {
                rem += k;
            }

            if(map.containsKey(rem)) {
                //if frequency is > 1, the subarray is divisible by k
                ans += map.get(rem);
                map.put(rem, map.get(rem) + 1);
            }
            else {
                map.put(rem, 1);
            }
        }
        return ans;
    }
}
```
