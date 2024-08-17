# Question

Given an integer array `nums`, return _the number of **subarrays** filled with 0_.

## Leetcode Link

[2348. Number of Zero-Filled Subarrays](https://leetcode.com/problems/number-of-zero-filled-subarrays/)

## Approach

The problem is to count the number of subarrays filled with zeros in an array. The key insight is that if you have a sequence of consecutive zeros of length n, the number of subarrays that can be formed from this sequence is n \* (n + 1) / 2. This is because:

A single 0 forms 1 subarray.
Two consecutive 0s form 3 subarrays: [0], [0], [0, 0].
Three consecutive 0s form 6 subarrays: [0], [0], [0], [0, 0], [0, 0], [0, 0, 0].

The code iterates through the array, counting consecutive zeros (consecutiveZeroes). For each zero, it adds the current count of consecutive zeros to count. This way, each time a zero is found, the possible subarrays including that zero are correctly added to the total count.

This approach has a time complexity of O(n) and a space complexity of O(1).

## Solution

```java
class Solution {
    public long zeroFilledSubarray(int[] nums) {
        long count = 0;
        long consecutiveZeroes = 0;

        for(int num : nums) {
            if(num == 0) {
                consecutiveZeroes++;
                count += consecutiveZeroes;
            } else {
                consecutiveZeroes = 0;
            }
        }

        return count;
    }
}
```
