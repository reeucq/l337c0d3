# Question

Given an array of integers `nums` sorted in non-decreasing order, find the starting and ending position of a given `target` value.

If `target` is not found in the array, return `[-1, -1]`.

You must write an algorithm with `O(log n)` runtime complexity.

## Leetcode Link

[34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

## Approaches

1. **Binary Search**: We can use binary search to find the lower and upper bounds of the target element. The lower bound will give us the starting position of the target element, and the upper bound will give us the position of the element just after the last occurrence of the target element, we can subtract 1 from the upper bound to get the ending position of the target element. We can check if the target is not equal to lower bound and return `[-1,-1]`. This has a time complexity of $O(log n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int start = getLowerBound(nums,target);
        if (start == -1 || nums[start] != target) return new int[]{-1, -1};
        int end = getUpperBound(nums, target) - 1;
        return new int[]{start, end};
    }

    public int getLowerBound(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;
        int ans = -1;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(nums[m] >= target) {
                ans = m;
                r = m - 1;
            } else {
                l = m + 1;
            }
        }

        return ans;
    }

    public int getUpperBound(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;
        int ans = nums.length;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(nums[m] > target) {
                ans = m;
                r = m - 1;
            } else {
                l = m + 1;
            }
        }

        return ans;
    }
}
```
