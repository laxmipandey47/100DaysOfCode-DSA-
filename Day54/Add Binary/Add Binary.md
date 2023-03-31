# 67. Add Binary

Given two binary strings `a` and `b`, return their sum as a binary string.

**Example 1:**
```
Input: a = "11", b = "1"
Output: "100"
```
**Example 2:**
```
Input: a = "1010", b = "1011"
Output: "10101"
``` 
**Constraints:**

* `1 <= a.length, b.length <= 104`
* `a` and `b` consist only of `'0'` or `'1'` characters.
* Each string does not contain leading zeros except for the zero itself.

**Solution:**
```
class Solution {
    public String addBinary(String a, String b) {
        //Approach: Starting from the last index of both string, storing the index value in x and y respectively
        //Calculating the resulting sum adding carry value (default as 0)
        //Getting the divisor of the resulting sum for updating the carry value

        int carry = 0;
        String ans = "";
        int i = 0;

        while(i < a.length() || i < b.length() || carry != 0) {
            int x = 0; //for storing the index value of string a
            if(i < a.length() && a.charAt(a.length() - 1 - i) == '1') {
                x = 1;
            }

            int y = 0; //for storing the index value of string b
            if(i < b.length() && b.charAt(b.length() - 1 - i) == '1') {
                y = 1;
            }

            ans = (x + y + carry) % 2 + ans;
            carry = (x + y + carry) / 2; //since its binary so divided by 2
            i++;
        }

        return ans;
    }
}
```
