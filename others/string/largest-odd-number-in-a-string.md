# Question

You are given a string `num`, representing a large integer. Return the _**largest-valued odd** integer (as a string) that is a **non-empty substring** of `num`, or an empty string `""` if no odd integer exists._

## Leetcode Link

[1903. Largest Odd Number in String](https://leetcode.com/problems/largest-odd-number-in-string/)

## Approaches

1. **Check for the first Odd Digit from Right Direction**: We'll iterate through the string from right to left and check for the first odd digit. If we find an odd digit, we'll return the substring from the start of the string to the index of the odd digit. If we don't find any odd digit, we'll return an empty string. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public String largestOddNumber(String num) {
        for(int i = num.length()-1; i >= 0; i--) {
            int c = num.charAt(i) - '0';
            if(c % 2 == 1) {
                return num.substring(0,i+1);
            }
        }
        return "";
    }
}
```
