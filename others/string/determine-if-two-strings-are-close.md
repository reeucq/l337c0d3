# Question

Two strings are considered **close** if you can attain one from the other using the following operations:

- Operation 1: Swap any two **existing** characters.
  - For example, `abcde -> aecdb`
- Operation 2: Transform **every** occurrence of one **existing** character into another **existing** character, and do the same with the other character.
  - For example, `aacabb -> bbcbaa` (all `a`'s turn into `b`'s, and all `b`'s turn into `a`'s)

You can use the operations on either string as many times as necessary.

Given two strings, `word1` and `word2`, return _`true` if `word1` and `word2` are **close**, and` false` otherwise._

## Leetcode Link

[1657. Determine if Two Strings Are Close](https://leetcode.com/problems/determine-if-two-strings-are-close/)

## Approaches

1. **Frequency Analysis**: For operation 1 we can check whether all the keys in the frequency dictionary of both strings are the same. For operation 2 we can check whether the values of the frequency dictionary of both strings are the same. If both conditions are satisfied then the strings are close. We can do this using two arrays since we know it'll only contain lowercase letters. The time complexity of this approach is $O(n)$ where n is the length of the string.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean closeStrings(String word1, String word2) {
        if(word1.length() != word2.length()) return false;

        int[] freq1 = new int[26];
        int[] freq2 = new int[26];

        for(char c : word1.toCharArray()) freq1[c-'a']++;
        for(char c : word2.toCharArray()) freq2[c-'a']++;

        for(int i = 0; i < 26; i++) {
            if((freq1[i] == 0 && freq2[i] != 0) || (freq1[i] != 0 && freq2[i] == 0)) {
                return false;
            }
        }

        Arrays.sort(freq1);
        Arrays.sort(freq2);

        return Arrays.equals(freq1,freq2);
    }
}
```
