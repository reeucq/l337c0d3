# Question

Given the array `nums` after the rotation and an integer `target`, return _`true` if `target` is in `nums`, or `false` if it is not in `nums`_. Note that `nums` may contain **duplicate elements**.

## Leetcode Link

[81. Search in Rotated Sorted Array II](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

## Approaches

1. **Binary Search**: We can directly apply the binary search algorithm on the rotated sorted array. We'll compare the target element with the middle element and then decide whether to search in the left half or the right half of the array. We'll keep on doing this until we find the target element or the left pointer crosses the right pointer. This will take `O(log n)` time. If we encounter duplicates we'll keep reducing the search space by moving the pointers.

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean search(int[] nums, int target) {
        int l = 0;
        int r = nums.length - 1;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(nums[m] == target) return true;

            // trim down the search space in case determining which portion of array is sorted isn't possible due to duplicates
            if(nums[l] == nums[m] && nums[m] == nums[r]) {
                l++;
                r--;
                continue;
            }

            if(nums[m] >= nums[l]) { // array is left sorted
            // now we'll check if our target lies between the left sorted portion or not
                if(nums[l] <= target && target <= nums[m]) {
                    r = m - 1;
                } else {
                    l = m + 1;
                }
            } else { // array is right sorted
            // now we'll check if our target lies between the right sorted portion or not
                if(nums[m] <= target && target <= nums[r]) {
                    l = m + 1;
                } else {
                    r = m - 1;
                }
            }
        }

        return false;
    }
}
```
