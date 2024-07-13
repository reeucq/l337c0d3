# Question

Given an array of integers `nums` and an integer `k`, return _the total number of subarrays whose sum equals to `k`._

A subarray is a contiguous **non-empty** sequence of elements within an array.

## Leetcode Link

[560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)

## Approaches

1. **Brute Force**: Generate all possible subarrays and check if the sum of the subarray is equal to `k`. Time complexity: $O(n^2)$, Space complexity: $O(1)$

2. **Hashing**: We use a running sum and a HashMap to keep track of the frequency of each sum encountered. The key insight is that if the current sum is sum, we're looking for how many times sum - k has occurred before. We initialize the map with {0: 1} to handle the case where the entire subarray from the start sums to k. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;
        for(int i = 0; i < nums.length; i++) {
            int sum = 0;
            for(int j = i; j < nums.length; j++) {
                sum += nums[j];
                if(sum == k) count++;
            }
        }
        return count;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        int count = 0;  // To store the number of subarrays with sum k
        int sum = 0;    // Running sum (cumulative sum)

        // HashMap to store the frequency of cumulative sums
        HashMap<Integer, Integer> sumFrequency = new HashMap<>();

        // Initialize the map with sum 0 occurring once
        // This handles the case where the entire subarray from the start sums to k
        sumFrequency.put(0, 1);

        for (int num : nums) {
            // Update the running sum
            sum += num;

            // If (sum - k) exists in the map, it means we've found a subarray with sum k
            // The value in the map tells us how many such subarrays end at the current position
            if (sumFrequency.containsKey(sum - k)) {
                count += sumFrequency.get(sum - k);
            }

            // Update the frequency of the current sum in the map
            sumFrequency.put(sum, sumFrequency.getOrDefault(sum, 0) + 1);
        }

        return count;
    }
}
```
