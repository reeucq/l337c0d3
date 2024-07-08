# Question

Given a binary array `nums`, return the maximum number of consecutive `1's` in the array.

## Leetcode Link

[485. Max Consecutive Ones](https://leetcode.com/problems/max-consecutive-ones/)

## Approaches

1. **Brute Force**: We can iterate over the array and keep track of the current consecutive ones. If we encounter a zero, we can reset the count. We can keep track of the maximum count as well. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

2. **Sliding Window**: We can use a sliding window approach to solve this problem. We can keep track of the start and end of the window and calculate the maximum length of the window. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int currentCount = 0;
        int maxCount = 0;

        for (int num : nums) {
            if (num == 1) {
                currentCount++;
                maxCount = Math.max(maxCount, currentCount);
            } else {
                currentCount = 0;
            }
        }

        return maxCount;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int start = 0;
        int end = 0;
        int maxCount = 0;

        while (end < nums.length) {
            if (nums[end] == 1) {
                end++;
                maxCount = Math.max(maxCount, end - start);
            } else {
                start = end + 1;
                end++;
            }
        }

        return maxCount;
    }
}
```
