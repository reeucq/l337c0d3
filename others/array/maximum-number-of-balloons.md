# Question

Given a string `text`, you want to use the characters of `text` to form as many instances of the word `"balloon"` as possible.

You can use each character in `text` **at most once**. Return _the maximum number of instances that can be formed._

## Leetcode Link

[1189. Maximum Number of Balloons](https://leetcode.com/problems/maximum-number-of-balloons/)

## Approaches

1. **Character Count**: Count the number of characters in the string and return the minimum count of the characters in the word "balloon".

2. **Character Count & Simulation**: Count the number of characters in the string and simulate the formation of the word "balloon" using the characters in the string.

## Solutions

### Java Approach 1

```java
class Solution {
    public int maxNumberOfBalloons(String text) {
        int b = 0, a = 0, l = 0, o = 0, n = 0;

        for (char c : text.toCharArray()) {
            switch (c) {
                case 'b': b++; break;
                case 'a': a++; break;
                case 'l': l++; break;
                case 'o': o++; break;
                case 'n': n++; break;
            }
        }

        return Math.min(b, Math.min(a, Math.min(l/2, Math.min(o/2, n))));
    }
}
```

### Java Approach 2

```java
class Solution {
    public int maxNumberOfBalloons(String text) {
        int[] cc = new int[26];
        for(char c : text.toCharArray()) cc[c-'a']++;
        int count = 0;

        while(cc['b'-'a'] > 0 && cc['a'-'a'] > 0 && cc['l'-'a'] > 1 && cc['o'-'a'] > 1 && cc['n'-'a'] > 0) {
            cc['b'-'a']--;
            cc['a'-'a']--;
            cc['l'-'a'] -= 2;
            cc['o'-'a'] -= 2;
            cc['n'-'a']--;
            count++;
        }

        return count;
    }
}
```
