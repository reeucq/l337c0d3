# Question

Given a **circular integer array** nums of length n, return _the maximum possible sum of a non-empty **subarray** of nums._

## Leetcode Link

[918. Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)

## Approaches

1. **Prefix & Suffix Sum**: This approach pre-computes the maximum suffix sums and then combines them with prefix sums in a single pass. The intuition is that any circular subarray can be formed by combining a prefix and a suffix. By maintaining a running prefix sum and comparing it with pre-computed maximum suffix sums, we can efficiently consider all possible circular subarrays without explicitly wrapping around the array. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

2. **Kadane's Algorithm**: The intuition is to consider two cases: (1) the maximum subarray doesn't wrap around, which we solve using Kadane's algorithm, and (2) it does wrap around. For the wrap-around case, we observe that it's equivalent to the total sum minus the minimum non-wrapping subarray sum. We find this by inverting the array and applying Kadane's algorithm again. The maximum of these two cases gives us our answer. It takes $O(n)$ time and $O(1)$ space.

## Solutions

### Java Approach 1

```java
class Solution {
    public int maxSubarraySumCircular(int[] nums) {
        final int n = nums.length;
        final int[] rightMax = new int[n];
        rightMax[n - 1] = nums[n - 1];
        int suffixSum = nums[n - 1];

        for (int i = n - 2; i >= 0; --i) {
            suffixSum += nums[i];
            rightMax[i] = Math.max(rightMax[i + 1], suffixSum);
        }

        int maxSum = nums[0];
        int specialSum = nums[0];
        int curMax = 0;
        for (int i = 0, prefixSum = 0; i < n; ++i) {
            // This is Kadane's algorithm.
            curMax = Math.max(curMax, 0) + nums[i];
            maxSum = Math.max(maxSum, curMax);

            prefixSum += nums[i];
            if (i + 1 < n) {
                specialSum = Math.max(specialSum, prefixSum + rightMax[i + 1]);
            }
        }

        return Math.max(maxSum, specialSum);
    }
}
```

### Java Approach 2

```java
class Solution {
    public int maxSubarraySumCircular(int[] nums) {
        int curMax = 0, curMin = 0;
        int globMax = nums[0], globMin = nums[0];
        int total = 0;
        for (int n : nums) {
            curMax = Math.max(curMax + n, n);
            curMin = Math.min(curMin + n, n);
            total += n;
            globMax = Math.max(curMax, globMax);
            globMin = Math.min(curMin, globMin);
        }
        return globMax > 0 ? Math.max(globMax, total - globMin) : globMax;
    }
}

```
