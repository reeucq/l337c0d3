# Question

Given an integer array `nums` of length `n` and an integer `target`, find three integers in `nums` such that the sum is closest to `target`.

Return _the sum of the three integers._

## Leetcode Link

[16. 3Sum Closest](https://leetcode.com/problems/3sum-closest/)

## Approaches

1. **Brute Force**: We can use three nested loops to iterate over all possible triplets and find the one with the sum closest to the target. This approach has a time complexity of $O(n^3)$.

2. **Two Pointers**: We can sort the array and then use two pointers to find the sum closest to the target. This approach has a time complexity of $O(n^2)$.

## Solutions

### Java Approach 1

```java
public int threeSumClosestBruteForce(int[] nums, int target) {
    int n = nums.length;
    int closestSum = nums[0] + nums[1] + nums[2];

    for (int i = 0; i < n - 2; i++) {
        for (int j = i + 1; j < n - 1; j++) {
            for (int k = j + 1; k < n; k++) {
                int sum = nums[i] + nums[j] + nums[k];
                if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                    closestSum = sum;
                }
            }
        }
    }

    return closestSum;
}
```

### Java Approach 2

```java
public int threeSumClosestTwoPointers(int[] nums, int target) {
    Arrays.sort(nums);
    int n = nums.length;
    int closestSum = nums[0] + nums[1] + nums[2];

    for (int i = 0; i < n - 2; i++) {
        int left = i + 1;
        int right = n - 1;

        while (left < right) {
            int sum = nums[i] + nums[left] + nums[right];

            if (sum == target) {
                return sum; // Exact match found
            }

            if (Math.abs(sum - target) < Math.abs(closestSum - target)) {
                closestSum = sum;
            }

            if (sum < target) {
                left++;
            } else {
                right--;
            }
        }
    }

    return closestSum;
}
```
