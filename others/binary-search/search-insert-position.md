# Question

Given a sorted array of distinct integers and a `target` value, return _the `index` if the `target` is found. If not, return the `index` where it would be if it were inserted in order._

You must write an algorithm with `O(log n)` runtime complexity

## Leetcode Link

[35. Search Insert Position](https://leetcode.com/problems/search-insert-position/)

## Approaches

1. **Binary Search**: Find the lower bound of the target element using binary search. Return the index of the lower bound. Note that lower bound is also known as the ceiling of the target element.

## Solutions

### Java Approach 1

```java
class Solution {
    public int searchInsert(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;
        int ans = nums.length;

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
}
```
