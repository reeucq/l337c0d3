# Question

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in` nums`. If `target` exists, then return _its index_. Otherwise, return `-1`.

## Leetcode Link

[704. Binary Search](https://leetcode.com/problems/binary-search/)

## Approaches

1. **Binary Search**: We can use binary search to find the target in the array. The time complexity of this approach is $O(\log n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int search(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(nums[m] == target) {
                return m;
            } else if(nums[m] < target) {
                l = m+1;
            } else {
                r = m-1;
            }
        }

        return -1;
    }
}
```
