# Question

Given a string `s`, return _the length of the longest substring between two equal characters, excluding the two characters. If there is no such substring return `-1`._

## Leetcode Link

[1624. Largest Substring Between Two Equal Characters](https://leetcode.com/problems/largest-substring-between-two-equal-characters/)

## Approaches

1. **HashMap**: We can use a hashmap to store the first and last occurrence of each character in the string. We can then iterate over the string and calculate the length of the substring between the first and last occurrence of each character. We can then return the maximum length of the substring. This approach has a time complexity of `O(n)` and a space complexity of `O(n)`.

## Solutions

```java
class Solution {
    public int maxLengthBetweenEqualCharacters(String s) {
        int[] cc = new int[26];
        Arrays.fill(cc,-1);
        int res = -1;
        for(int i = 0; i < s.length(); i++) {
            if(cc[s.charAt(i) - 'a'] == -1) {
                cc[s.charAt(i) - 'a'] = i;
            } else {
                res = Math.max(res, i - cc[s.charAt(i) - 'a'] + 1);
            }
        }
        return res == -1 ? res : res - 2;
    }
}
```
