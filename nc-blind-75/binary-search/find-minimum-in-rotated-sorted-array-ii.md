# Question

Given the sorted rotated array `nums` that may contain **duplicates**, return _the minimum element of this array._

## Leetcode Link

[154. Find Minimum in Rotated Sorted Array II](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)

## Approaches

1. **Binary Search**: We can use binary search to find the minimum element in the rotated sorted array. The idea is to find the pivot element, which is the minimum element in the array. The pivot element is the only element in the array that is smaller than its previous element. We can find the pivot element by comparing the middle element with the last element of the array. If the middle element is greater than the last element, then the pivot element is on the right side of the middle element. Otherwise, the pivot element is on the left side of the middle element. We can then adjust the search space accordingly and continue the search until we find the pivot element. The time complexity of this approach is $O(log n)$, where n is the number of elements in the array. These solutions also work when the array doesn't contain duplicates.

## Solutions

### Java Approach 1 - Sol 1

```java
class Solution {
    public int findMin(int[] nums) {
        int l = 0;
        int r = nums.length - 1;
        int m = 0;

        while(l <= r) {
            m = l + (r - l)/2;

            if(nums[m] > nums[r]) {
                l = m + 1;
            } else if(nums[m] < nums[r]) {
                r = m;
            } else {
                r--;
            }
        }

        return nums[m];
    }
}
```

### Java Approach 1 - Sol 2

```java
class Solution {
    public int findMin(int[] nums) {
        int l = 0;
        int r = nums.length - 1;
        int ans = Integer.MAX_VALUE;

        while(l <= r) {
            int m = l + (r - l)/2;

            if(nums[m] < nums[r]) {
                // right portion is sorted
                ans = Math.min(ans, nums[m]);
                r = m - 1;
            } else if(nums[m] > nums[r]) {
                // left portion is sorted
                ans = Math.min(ans, nums[l]);
                l = m + 1;
            } else {
                // nums[m] == nums[r]
                ans = Math.min(ans, nums[m]);
                r--;
            }
        }

        return ans;
    }
}
```
