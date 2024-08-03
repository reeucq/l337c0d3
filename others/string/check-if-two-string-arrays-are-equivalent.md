# Question

Given two string arrays `word1` and `word2`, return `true` _if the two arrays **represent** the same string, and `false` otherwise._

## Leetcode Link

[1662. Check If Two String Arrays are Equivalent](https://leetcode.com/problems/check-if-two-string-arrays-are-equivalent/)

## Approaches

1. **Join and Compare**: This approach joins the strings in both arrays and compares them.

   - Time complexity: O(n)
   - Space complexity: O(n)

2. **Two Pointers**: This approach uses two pointers to iterate over the characters of the strings in both arrays.
   - Time complexity: O(n)
   - Space complexity: O(1)

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        return String.join("",word1).equals(String.join("",word2));
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean arrayStringsAreEqual(String[] word1, String[] word2) {
        int i = 0;
        int j = 0;
        for(int ii = 0, jj = 0; i < word1.length && j < word2.length;) {
            if(word1[i].charAt(ii++) != word2[j].charAt(jj++)) return false;
            if(ii == word1[i].length()) {
                i++;
                ii = 0;
            }
            if(jj == word2[j].length()) {
                j++;
                jj = 0;
            }
        }
        return i == word1.length && j == word2.length;
    }
}
```
