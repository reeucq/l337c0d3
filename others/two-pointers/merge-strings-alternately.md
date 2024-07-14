# Question

You are given two strings `word1` and `word2`. Merge the strings by adding letters in alternating order, starting with `word1`. If a string is longer than the other, append the additional letters onto the end of the merged string.

Return _the merged string._

## Leetcode Link

[1768. Merge Strings Alternately](https://leetcode.com/problems/merge-strings-alternately/)

## Approaches

1. **Two Pointers**: We can use two pointers to iterate over the two strings and append the characters alternatively to the result string. We can also append the remaining characters of the longer string to the result string. This approach has a time complexity of O(n+m) and a space complexity of O(n+m), where n and m are the lengths of the two strings.

## Solutions

### Java Approach 1

```java
class Solution {
    public String mergeAlternately(String word1, String word2) {
        int i = 0;
        StringBuilder res = new StringBuilder();

        while (i < word1.length() || i < word2.length()) {
            if (i < word1.length()) {
                res.append(word1.charAt(i));
            }
            if (i < word2.length()) {
                res.append(word2.charAt(i));
            }
            i++;
        }

        return res.toString();
    }
}
```
