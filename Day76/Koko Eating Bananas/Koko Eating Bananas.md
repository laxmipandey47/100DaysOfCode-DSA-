# 875. Koko Eating Bananas

Koko loves to eat bananas. There are `n` piles of bananas, the `ith` pile has `piles[i]` bananas. The guards have gone and will come back in `h` hours.

Koko can decide her bananas-per-hour eating speed of `k`. Each hour, she chooses some pile of bananas and eats `k` bananas from that pile. If the pile has less than `k` bananas, she eats all of them instead and will not eat any more bananas during this hour.

Koko likes to eat slowly but still wants to finish eating all the bananas before the guards return.

Return the minimum integer `k` such that she can eat all the bananas within `h` hours.

**Example 1:**
```
Input: piles = [3,6,7,11], h = 8
Output: 4
```
**Example 2:**
```
Input: piles = [30,11,23,4,20], h = 5
Output: 30
```
**Example 3:**
```
Input: piles = [30,11,23,4,20], h = 6
Output: 23
``` 
**Constraints:**

* `1 <= piles.length <= 104`
* `piles.length <= h <= 109`
* `1 <= piles[i] <= 109`

**Solution:**
```
class Solution {
    public int minEatingSpeed(int[] piles, int h) {
        //Approach: Applying Binary Search for the speed starting from the lowest to highest element value to get the minimium speed of eating banana per hour

         int low=1,high=1_000_000_000;
          while(low<high){
                  int mid=low + (high-low)/2;
                  if(isPossible(piles,h,mid)){
                          high=mid;
                  }
                  else{
                          low=mid+1;
                  }
          }
          return low;
    }

    public boolean isPossible(int[] piles, int h, int k) {
        int time=0;
            for(int p:piles){
                  time+=(p-1)/k+1;
                  if(time>h) break;
            }
            return time<=h;
    }
}
```
