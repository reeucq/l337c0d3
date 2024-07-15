# Question

Given two strings `s1` and `s2`, return `true` if `s2` contains a permutation of `s1`, or `false` otherwise.

In other words, return `true` if one of `s1's` permutations is the substring of `s2`.

## Leetcode Link

[576. Permutation in String](https://leetcode.com/problems/permutation-in-string/)

## Approaches

1. **Using Sliding Window and Extra Space**: We'll create a character frequency array of string `s1`. Then we'll check each possible substring of length `s1` and create its character frequency array. If both arrays are equal, we'll return `true`. Otherwise, we'll move the window and repeat the process. If we don't find any substring, we'll return `false`. Time Complexity $O(l1 + (l2-l1+1) * l1)$, where `l1` is the length of `s1` and `l2` is the length of `s2`, and Space Complexity $O(1)$ since we use fixed size arrays.

2. **Using Sliding Window Without Extra Space**: We'll create two character frequency arrays of string `s1` and `s2` and a `matches` variable which tells us how much matches are there between both the character frequency arrays of `s1` and `s2`. We'll iterate over the string `s2` and add and remove characters from the character frequency arrays of `s2` and update the `matches` variable. If at any point out `matches` variable is equal to the length of `26`, we'll return `true`. Otherwise, we'll move the window and repeat the process. If we don't find any substring, we'll return `false`. Time Complexity $O(l1 + l2)$ and Space Complexity $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        int[] charCount = new int[26];
        for(char c : s1.toCharArray()) charCount[c-'a']++;

        for(int i = 0; i <= s2.length() - s1.length(); i++) {
            String sub = s2.substring(i,i+s1.length());
            if(charCount[sub.charAt(0)-'a'] > 0) {
                int[] temp = new int[26];
                for(char c : sub.toCharArray()) {
                    temp[c-'a']++;
                }
                if(Arrays.equals(temp,charCount)) return true;
            }
        }

        return false;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean checkInclusion(String s1, String s2) {
        if (s1.length() > s2.length()) return false;

        int[] s1Count = new int[26];
        int[] s2Count = new int[26];

        // Count characters for the first window
        for (int i = 0; i < s1.length(); i++) {
            s1Count[s1.charAt(i) - 'a']++;
            s2Count[s2.charAt(i) - 'a']++;
        }

        int matches = 0;
        for (int i = 0; i < 26; i++) {
            if (s1Count[i] == s2Count[i]) matches++;
        }

        int left = 0;
        for (int right = s1.length(); right < s2.length(); right++) {
            if (matches == 26) return true;

            // Add a character to the window
            int index = s2.charAt(right) - 'a';
            s2Count[index]++;
            if (s2Count[index] == s1Count[index]) {
                matches++;
            } else if (s2Count[index] == s1Count[index] + 1) {
                matches--;
            }

            // Remove a character from the window
            index = s2.charAt(left) - 'a';
            s2Count[index]--;
            if (s2Count[index] == s1Count[index]) {
                matches++;
            } else if (s2Count[index] == s1Count[index] - 1) {
                matches--;
            }
            left++;
        }

        return matches == 26;
    }
}
```
