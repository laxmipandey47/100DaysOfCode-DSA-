# 438. Find All Anagrams in a String

Given two strings `s` and `p`, return an array of all the start indices of `p`'s anagrams in `s`. You may return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

**Example 1:**
```
Input: s = "cbaebabacd", p = "abc"
Output: [0,6]
Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```
**Example 2:**
```
Input: s = "abab", p = "ab"
Output: [0,1,2]
Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

**Constraints:**

* `1 <= s.length, p.length <= 3 * 104`
* `s` and `p` consist of lowercase English letters.

**Solution:**
```
class Solution {
    public List<Integer> findAnagrams(String s, String p) {
        //Creating two count arrays for s and p, checking for every i element in s till size of p
        //if all the element count are same adding the starting index to ans list and incrementing the count of i(th) element and changing the (i - size of p) element to check for next three elements
        List<Integer> ans = new ArrayList<>();
        if(p.length() > s.length()) {
            return ans;
        }

        int sl = s.length();
        int pl = p.length();

        int[] countOfP = updateCount(p);
        int[] countOfS = updateCount(s.substring(0,pl));

        if(countSame(countOfP, countOfS)) {
            ans.add(0);
        }

        for(int i = pl; i < sl; i++) {
            countOfS[s.charAt(i - pl) - 'a']--;
            countOfS[s.charAt(i) - 'a']++;
            if(countSame(countOfP, countOfS)) {
                ans.add(i - pl + 1);
            }
        }

        return ans;
    }

    private int[] updateCount(String s) {
        int[] count = new int[26];
        for(int i = 0; i< s.length(); i++) {
            count[s.charAt(i) - 'a']++;
        }

        return count;
    }

    private boolean countSame(int[] x, int[] y) {
        for(int i = 0; i< 26; i++) {
            if(x[i] != y[i]) {
                return false;
            }
        }
        return true;
    }
}
```
