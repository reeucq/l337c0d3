# Question

Given a binary string `s`, return _the number of substrings with all characters `1's`_. Since the answer may be too large, return it modulo `10^9 + 7`.

## Leetcode Link

[1513. Number of Substrings With Only 1s](https://leetcode.com/problems/number-of-substrings-with-only-1s/)

## Approach

The algorithm counts the number of substrings containing only '1's in a binary string. The key idea is that each consecutive sequence of '1's contributes to several substrings. For each '1' encountered, it adds the length of the current sequence of '1's to the total count, reflecting all substrings ending at that position. The modulo operation ensures the result fits within standard integer limits.

## Solution

```java
class Solution {
    public int numSub(String s) {
        long count = 0;
        long consecutiveOnes = 0;
        int mod = 1000000007;

        for (char c : s.toCharArray()) {
            if (c == '1') {
                consecutiveOnes++;
                count += consecutiveOnes;
            } else {
                consecutiveOnes = 0;
            }
        }

        return (int) (count % mod);
    }
}
```
