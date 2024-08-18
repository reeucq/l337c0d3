# Question

Given a string `s`, return _the number of **homogenous** substrings of `s`_. Since the answer may be too large, return it **modulo** `10^9 + 7`.

## Leetcode Link

[1759. Count Number of Homogeneous Substrings](https://leetcode.com/problems/count-number-of-homogenous-substrings/)

## Approach

This algorithm counts the number of homogenous substrings in a string, where a homogenous substring consists of identical characters. For each character, it checks if it's the same as the previous one. If so, it extends the current sequence of identical characters, adding the length of this sequence to the total count (reflecting all possible homogenous substrings ending at that character). If the character is different, it starts a new sequence. The modulo operation ensures the result remains within integer bounds.

## Solution

```java
class Solution {
    public int countHomogenous(String s) {
        long count = 0;
        long consecutives = 0;
        char prevChar = '\0';
        int mod = 1000000007;

        for(char c : s.toCharArray()) {
            if(c == prevChar) {
                consecutives++;
            } else {
                consecutives = 1;
                prevChar = c;
            }
            count += consecutives;
        }

        return (int) (count % mod);
    }
}
```
