# 1137. N-th Tribonacci Number

The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

 
**Example 1:**
```
Input: n = 4
Output: 4
Explanation:
T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
```
**Example 2:**
```
Input: n = 25
Output: 1389537
```

**Constraints:**

* `0 <= n <= 37`
* The answer is guaranteed to fit within a 32-bit integer, ie. `answer <= 2^31 - 1`.

**Solution:** 

```
class Solution {
    public int tribonacci(int n) {
        int[] trib = new int[n + 1];
        return tribo(n, trib);
    }

    int tribo(int num, int[] trib) {
        if (num == 0) return 0;
        if (num == 1 || num == 2) return 1;

        if (trib[num] != 0) {
            return trib[num];    
        }
        trib[num] = tribo(num - 1, trib) + tribo(num - 2, trib) + tribo(num - 3, trib);  
        return trib[num];
    }
}
```
