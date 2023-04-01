# 28. Find the Index of the First Occurrence in a String

Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle` in `haystack`, or `-1` if `needle` is not part of `haystack`.

**Example 1:**
```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
```
**Example 2:**
```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
``` 

**Constraints:**

* `1 <= haystack.length, needle.length <= 104`
* `haystack` and `needle` consist of only lowercase English characters.

Solution:
```
class Solution {
    public int strStr(String haystack, String needle) {
        //Approach: Iterating throughout the haystack string, checking if the first character of the needle string matches to the haystack string character
        //if it matches, check for match of the complete substring, if so return i else return -1 
        for(int i = 0; i < haystack.length() - needle.length() + 1; i++) {
            if(haystack.charAt(i) == needle.charAt(0)) {
                //Since substring method checks inclusive of the second index parameter
                //Here, starts from 3 and ends with 3 + 3 = 6
                if(haystack.substring(i, needle.length() + i).equals(needle)) {
                    return i;
                }
            }
        } 
        return -1;
    }
}
```
