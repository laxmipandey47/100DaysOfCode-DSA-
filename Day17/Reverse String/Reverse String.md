# 344. Reverse String

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array in-place with `O(1)` extra memory.

**Example 1:**
```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```
**Example 2:**
```
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
``` 

**Constraints:**

* ```1 <= s.length <= 105```
* ```s[i] is a printable ascii character.```

**Solution:** 
```
class Solution {
    public void reverseString(char[] s) {
        recursive(s, 0, s.length - 1);
    }

    //function to reverse string using recursion
    private void recursive(char[] s, int start, int end) {
        if(start > end) {
            return;
        }
        char temp = s[start];
        s[start] = s[end];
        s[end] = temp;

        recursive(s, start + 1, end - 1);
    }
}
```
