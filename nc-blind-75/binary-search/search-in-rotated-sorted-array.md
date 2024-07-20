# Question

Given the array `nums` after the possible rotation and an integer `target`, return the `index` of `target` if it is in `nums`, or `-1` if it is not in `nums`.

## Leetcode Link

[33. Search in Rotated Sorted Array](https://leetcode.com/problems/search-in-rotated-sorted-array/)

## Approaches

1. **Finding the Pivot and Binary Search**: We'll find the pivot element in the rotated sorted array and then use that pivot to find the real middle elements and compare it with the target element. If the target element is greater than the middle element, we'll search in the right half of the array, else we'll search in the left half of the array. We'll keep on doing this until we find the target element or the left pointer crosses the right pointer. This will take `O(2log n)` time.

2. **Using Direct Binary Search**: We can directly apply the binary search algorithm on the rotated sorted array. We'll compare the target element with the middle element and then decide whether to search in the left half or the right half of the array. We'll keep on doing this until we find the target element or the left pointer crosses the right pointer. This will take `O(log n)` time.

## Solutions

### Java Approach 1

```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums == null || nums.length == 0) return -1;

        int l = 0;
        int r = nums.length - 1;
        int m = 0;

        while(l <= r) {
            m = l + (r-l)/2;

            if(nums[m] < nums[r]) {
                r = m;
            } else {
                l = m+1;
            }
        }

        int pivot = m;

        // reset the boundries
        l = 0;
        r = nums.length - 1;

        while(l <= r) {
            m = l + (r-l)/2;
            int realM = (m + pivot) % nums.length;

            if(nums[realM] == target) return realM;
            else if(nums[realM] < target) l = m + 1;
            else r = m - 1;
        }

        return -1;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int search(int[] nums, int target) {
        if (nums == null || nums.length == 0) return -1;

        int l = 0;
        int r = nums.length - 1;

        while(l <= r) {
            int m = l + (r - l)/2;

            if(nums[m] == target) return m;
            else if(nums[m] >= nums[l]) { // array is left sorted
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

        return -1;
    }
}
```
