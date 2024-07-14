# Question

Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string `""`.

## Leetcode Link

[14. Longest Common Prefix](https://leetcode.com/problems/longest-common-prefix/)

## Approaches

1. **Horizontal scanning**: This approach scans the strings horizontally. We take the first string as our initial prefix and then iterate through the remaining strings, shortening the prefix as needed until we find the longest common prefix. O(S) time, where S is the sum of all characters in all strings. O(1) extra space.

2. **Vertical scanning**: Instead of matching the whole prefix, we match character by character vertically across all strings. We stop when we find a mismatch or reach the end of a string. O(S) time, but can be faster in practice for cases where strings differ early. O(1) extra space.

## Solutions

### Java Approach 1

```java
public class Solution {
    public String longestCommonPrefix(String[] strs) {
        if (strs == null || strs.length == 0) {
            return "";
        }

        // Take the first string as the initial prefix
        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++) {
            // While the current string doesn't start with the prefix
            while (strs[i].indexOf(prefix) != 0) {
                // Shorten the prefix by one character
                prefix = prefix.substring(0, prefix.length() - 1);

                // If the prefix becomes empty, there is no common prefix
                if (prefix.isEmpty()) {
                    return "";
                }
            }
        }

        return prefix;
    }
}
```

### Java Approach 2

```java
class Solution {
    public String longestCommonPrefix(String[] strs) {
        StringBuilder res = new StringBuilder();

        for(int i = 0; i < strs[0].length(); i++) {
            for(String s : strs) {
                if(i == s.length() || s.charAt(i) != strs[0].charAt(i)) {
                    return res.toString();
                }
            }
            res.append(strs[0].charAt(i));
        }

        return res.toString();
    }
}
```
