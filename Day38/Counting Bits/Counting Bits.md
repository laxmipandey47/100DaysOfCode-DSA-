# 338. Counting Bits

Given an integer n, return an array ans of length n + 1 such that for each i (0 <= i <= n), ans[i] is the number of 1's in the binary representation of i.

 
**Example 1:**
```
Input: n = 2
Output: [0,1,1]
Explanation:
0 --> 0
1 --> 1
2 --> 10
```
**Example 2:**
```
Input: n = 5
Output: [0,1,1,2,1,2]
Explanation:
0 --> 0
1 --> 1
2 --> 10
3 --> 11
4 --> 100
5 --> 101
``` 

**Constraints:**

* `0 <= n <= 105`

**Solution:**
```
class Solution {
    public int[] countBits(int n) {
        int[] ans = new int[n + 1];

        for(int i = 0; i <= n; i++) {
            ans[i] = count(i);
        }

        return ans;
    }

    private int count(int num) {
        if(num == 0) {
            return 0;
        }
        if(num == 1) {
            return 1;
        }

        if(num % 2 == 0) {
            //since the number contains same set bits as num/2
            return count(num/2);
        }
        else {
            //since the number contains +1 set bits as in num/2 
            return 1 + count(num/2);
        }
    }
}
```
