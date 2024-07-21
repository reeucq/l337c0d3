# Question

You are given a string `num` representing a large integer. An integer is **good** if it meets the following conditions:

- It is a **substring** of `num` with length `3`.
- It consists of only one unique digit.

Return _the **maximum good** integer as a **string** or an empty string `""` if no such integer exists._

## Leetcode Link

[2264. Largest 3-Same-Digit Number in String](https://leetcode.com/problems/largest-3-same-digit-number-in-string/)

## Approaches

1. **Sliding Window**: Use a sliding window of size `3` to find the maximum good integer.

## Solutions

### Java Approach 1

```java
class Solution {
    public String largestGoodInteger(String num) {
        String max = "";
        for(int i = 0; i <= num.length() - 3; i++) {
            String sub = num.substring(i,i+3);
            if(isValid(sub) && sub.compareTo(max) > 0) {
                max = sub;
            }
        }
        return max;
    }

    private boolean isValid(String s) {
        return s.charAt(0) == s.charAt(1) && s.charAt(1) == s.charAt(2);
    }
}
```
