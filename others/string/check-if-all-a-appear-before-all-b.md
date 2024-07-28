# Question

Given a string `s` consisting of **only** the characters `'a'` and `'b'`, return _`true` if every `'a'` appears before every `'b'` in the string. Otherwise, return `false`._

## Leetcode Link

[2124. Check if All the 'a's Appear Before All the 'b's in the String](https://leetcode.com/problems/check-if-all-as-appears-before-all-bs/)

## Approaches

1. **Substring Check**: We can check if the string `s` contains any substring `"ba"`. If it does, we return `false`; otherwise, we return `true`. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

2. **Brute Force**: We can iterate through the string `s` and check if any `'a'` appears after a `'b'`. If it does, we return `false`; otherwise, we return `true`. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean checkString(String s) {
        return !s.contains("ba");
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean checkString(String s) {
        boolean foundB = false;
        for(char c : s.toCharArray()) {
            if(c == 'b') foundB = true;
            if(foundB) if(c == 'a') return false;
        }
        return true;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean checkString(String s) {
        for (int i = 1; i < s.length(); ++i)
            if (s.charAt(i - 1) == 'b' && s.charAt(i) == 'a')
                return false;
        return true;
    }
}
```
