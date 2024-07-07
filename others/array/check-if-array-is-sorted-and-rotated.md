# Question

Given an array `nums`, return `true` _if the array was originally sorted in non-decreasing order, then rotated **some** number of positions (including zero)_. Otherwise, return `false`.

There may be **duplicates** in the original array.

## Leetcode Link

[1752. Check if Array Is Sorted and Rotated](https://leetcode.com/problems/check-if-array-is-sorted-and-rotated/)

## Approaches

1. **Brute Force**: In this approach, we will check for all possible rotations of the array and check if the array is sorted or not. If we find any rotation where the array is sorted, we will return `true`. Otherwise, we will return `false`. The time complexity of this approach is O(n^2) where n is the number of elements in the array.

2. **Optimal Approach**: In this approach, we will find the number of rotations required to sort the array. If the number of rotations is 0 or 1, then the array is sorted. Otherwise, the array is not sorted. The time complexity of this approach is O(n) where n is the number of elements in the array.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean check(int[] nums) {
        int n = nums.length;

        for (int start = 0; start < n; start++) {
            boolean isSorted = true;

            for (int i = 0; i < n - 1; i++) {
                if (nums[(start + i) % n] > nums[(start + i + 1) % n]) {
                    isSorted = false;
                    break;
                }
            }

            if (isSorted) {
                return true;
            }
        }

        return false;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean check(int[] nums) {
        int n = nums.length;
        int count = 0;

        for(int i = 0; i < n; i++) {
            System.out.println(i);
            if(nums[i] > nums[(i+1)%n]) count++;
            if(count > 1) return false;
        }

        return true;
    }
}
```
