# Question

Given two strings `s` and `goal`, return _`true` if and only if `s` can become `goal` after some number of shifts on `s`._

## Leetcode Link

[796. Rotate String](https://leetcode.com/problems/rotate-string/)

## Approaches

1. **Brute Force**: This approach simply simulates the rotation process, checking at each step if the rotated string matches the goal. Time complexity is $O(n^2)$ and space complexity is $O(n)$.

2. **Check Concatenation**: This approach checks if the goal is a substring of the concatenation of `s` with itself. Time complexity is $O(n)$ and space complexity is $O(n)$.

3. **KMP Algorithm**: This approach uses the Knuth-Morris-Pratt algorithm to check if the goal is a substring of the concatenation of `s` with itself. Time complexity is $O(n)$ and space complexity is $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution1 {
    public boolean rotateString(String s, String goal) {
        if (s.length() != goal.length()) return false;
        if (s.length() == 0) return true;

        for (int i = 0; i < s.length(); i++) {
            if (s.equals(goal)) return true;
            s = s.substring(1) + s.charAt(0);
        }
        return false;
    }
}
```

### Java Approach 2

```java
class Solution2 {
    public boolean rotateString(String s, String goal) {
        return s.length() == goal.length() && (s + s).contains(goal);
    }
}
```
