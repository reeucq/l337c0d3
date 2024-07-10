# Description

There is a biker going on a road trip. The road trip consists of `n + 1` points at different altitudes. The biker starts his trip on point `0` with altitude equal `0`.

You are given an integer array `gain` of length `n` where `gain[i]` is the **net gain in altitude** between points `i`​​​​​​ and `i + 1` for all `(0 <= i < n)`. Return _the **highest altitude** of a point_.

## Leetcode Link

[1732. Find the Highest Altitude](https://leetcode.com/problems/find-the-highest-altitude/)

## Approaches

1. **Prefix Sum**: We can calculate the prefix sum of the array and return the maximum value. This is because the prefix sum at any index `i` will give us the altitude at that point. This approach has a time complexity of $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int largestAltitude(int[] gain) {
        int max = gain[0];
        for(int i = 1; i < gain.length; i++) {
            gain[i] += gain[i-1];
            if(gain[i] > max) max = gain[i];
        }
        return max > 0 ? max : 0;
    }
}
```
