# 567. Permutation in String

Given two strings `s1` and `s2`, return `true` if `s2` contains a permutation of `s1`, or `false` otherwise.

In other words, return `true` if one of `s1`'s permutations is the substring of `s2`.

**Example 1:**
```
Input: s1 = "ab", s2 = "eidbaooo"
Output: true
Explanation: s2 contains one permutation of s1 ("ba").
```
**Example 2:**
```
Input: s1 = "ab", s2 = "eidboaoo"
Output: false 
```

**Constraints:**

* `1 <= s1.length, s2.length <= 104`
* `s1` and `s2` consist of lowercase English letters.

**Solution:**
```
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        //Setting the values of string1 element as 1 and string2 element as -1
        //in a count array, if the value of count elements evaluates to zero for all elements of string1 return true else return false 
        int size1 = s1.length();
        int size2 = s2.length();

        if(size1 > size2) {
            return false;
        }

        int[] count = new int[26];
        for(int i = 0; i < size1; i++) {
            count[s1.charAt(i) - 'a']++;
        }

        for(int i = 0; i < size2; i++) {
            count[s2.charAt(i) - 'a']--;
            if( i - size1 >= 0) {
                count[s2.charAt(i - size1) - 'a']++;
            }

            if(allCountZero(count)) {
                return true;
            } 
        }
        return false;
    }

        private boolean allCountZero(int[] count) {
            for(int i = 0; i < 26; i++) {
                if(count[i] != 0) {
                    return false;
                }
            }
            return true;
        }
}
```
