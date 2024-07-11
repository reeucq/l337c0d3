# Question

Given an integer array `nums`, find the subarray with the largest sum, and return _its sum_.

## Leetcode Link

[53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

## Approaches

1. **Brute Force**: We can find all possible subarrays and calculate their sum. The subarray with the largest sum will be our answer. This approach will take $O(n^2)$ time.

2. **Kadane's Algorithm**: We can use Kadane's algorithm to solve this problem in $O(n)$ time.

## Solutions

### Java Approach 1

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = nums[0];
        for (int i = 0; i < nums.length; i++) {
            int sum = 0;
            for (int j = i; j < nums.length; j++) {
                sum += nums[j];
                maxSum = Math.max(sum, maxSum);
            }
        }
        return maxSum;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int maxSum = Integer.MIN_VALUE;
        int currentSum = 0;
        for(int x : nums) {
            currentSum = Math.max(x, currentSum + x);
            maxSum = Math.max(maxSum, currentSum);
        }
        return maxSum;
    }
}

```

### Follow-Up - Also find the Max Subarray

```java
class Solution {
    public int[] maxSubArray(int[] nums) {
        int maxSum = nums[0];
        int currentSum = nums[0];
        int start = 0, end = 0, tempStart = 0;

        for(int i = 1; i < nums.length; i++) {
            if (currentSum + nums[i] < nums[i]) {
                currentSum = nums[i];
                tempStart = i;
            } else {
                currentSum += nums[i];
            }

            if (currentSum > maxSum) {
                maxSum = currentSum;
                start = tempStart;
                end = i;
            }
        }

        // Extract the subarray from start to end (inclusive)
        int[] resultSubArray = new int[end - start + 1];
        for (int i = start; i <= end; i++) {
            resultSubArray[i - start] = nums[i];
        }

        return resultSubArray;
    }
}

```
