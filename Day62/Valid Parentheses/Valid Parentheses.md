# 20. Valid Parentheses

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.<br>
Open brackets must be closed in the correct order.<br>
Every close bracket has a corresponding open bracket of the same type.
 
**Example 1:**
```
Input: s = "()"
Output: true
```
**Example 2:**
```
Input: s = "()[]{}"
Output: true
```
**Example 3:**
```
Input: s = "(]"
Output: false
``` 

**Constraints:**

`1 <= s.length <= 104`
`s` consists of parentheses only `'()[]{}'`.

**Solution:**
```
class Solution {
    public boolean isValid(String s) {
        // Stack to store left symbols
        Stack<Character> leftSymbols = new Stack<>();
        // Loop for each character of the string
        for (char c : s.toCharArray()) {
            // If left symbol is encountered
            if (c == '(' || c == '{' || c == '[') {
                leftSymbols.push(c);
            }
            // If right symbol is encountered
            else if (c == ')' && !leftSymbols.isEmpty() && leftSymbols.peek() == '(') {
                leftSymbols.pop();
            } else if (c == '}' && !leftSymbols.isEmpty() && leftSymbols.peek() == '{') {
                leftSymbols.pop();
            } else if (c == ']' && !leftSymbols.isEmpty() && leftSymbols.peek() == '[') {
                leftSymbols.pop();
            }
            // If none of the valid symbols is encountered
            else {
                return false;
            }
        }
        return leftSymbols.isEmpty();
    }
}
```
