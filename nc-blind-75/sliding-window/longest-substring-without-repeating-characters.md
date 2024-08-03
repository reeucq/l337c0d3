# Question

Given a string `s`, find the length of the **longest** substring without repeating characters.

## Leetcode Link

[3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

## Approaches

1. **Brute Force**: We can generate all possible substrings of the given string and check if each substring has all unique characters. We can keep track of the length of the longest substring found so far. This approach has a time complexity of `O(n^3)`.

2. **Sliding Window**: We can use a sliding window to keep track of the characters in the current substring. We can maintain an array to store the count of each character in the current substring. We can use two pointers to keep track of the start and end of the current substring. When we encounter a character that is already present in the current substring, we can move the start pointer to the right until the character is no longer present in the current substring. This approach has a time complexity of `O(n)`.

## Solutions

### Java Approach 1

```java
public static int lengthOfLongestSubstring(String s) {
    int n = s.length();
    int maxLen = 0;

    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j <= n; j++) {
            if (allUnique(s, i, j)) {
                maxLen = Math.max(maxLen, j - i);
            }
        }
    }
    return maxLen;
}

private static boolean allUnique(String s, int start, int end) {
    boolean[] chars = new boolean[128]; // Assuming ASCII 128
    for (int i = start; i < end; i++) {
        char c = s.charAt(i);
        if (chars[c]) {
            return false;
        }
        chars[c] = true;
    }
    return true;
}
```

### Java Approach 2

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int[] count = new int[256];

        int start = 0;
        int end = 0;
        int max = 0;
        while(end < s.length()) {
            count[s.charAt(end)]++;

            while(count[s.charAt(end)] > 1) {
                count[s.charAt(start)]--;
                start++;
            }

            max = Math.max(max, end - start + 1);
            end++;
        }

        return max;
    }
}
```

### Java Approach 3 - Deque

```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Deque<Character> dq = new LinkedList<>();
        int max = 0;

        for(char c : s.toCharArray()) {
            while(dq.contains(c)) dq.pollFirst();
            dq.add(c);
            max = Math.max(max, dq.size());
        }

        return max;
    }
}
```
