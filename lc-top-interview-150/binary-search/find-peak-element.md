# Question

A peak element is an element that is strictly greater than its neighbors. Given a **0-indexed** integer array `nums`, find a peak element, and return its index. If the array contains multiple peaks, return the index to **any of the peaks**.

You may imagine that `nums[-1] = nums[n] = -∞`. In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

## Leetcode Link

[162. Find Peak Element](https://leetcode.com/problems/find-peak-element/)

## Approaches

1. **Linear Search**: We can iterate over the array and check if the current element is greater than its neighbors. If it is, we return the index of the current element. This approach has a time complexity of $O(n)$.

2. **Binary Search**: We can use binary search to find the peak element. We start by finding the middle element of the array. If the middle element is greater than its neighbors, we return the index of the middle element. Otherwise, we move towards the side with the higher neighbor, this works because we know that the peak element will be on the side with the higher neighbor, because it's alr greater than its left neighbor (mid) and it is guaranteed to be greater than its right neighbor (if somehow we each any of the extreme points, since they are already given as being greater than their neighbors). This approach has a time complexity of $O(\log n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int findPeakElement(int[] nums) {
        if(nums.length == 1) return 0;
        if(nums[0] > nums[1]) return 0;
        if(nums[nums.length - 1] > nums[nums.length - 2]) return nums.length - 1;

        int l = 0;
        int r = nums.length - 1;
        while(l <= r) {
            int mid = l + (r-l)/2;

            if((mid-1 < 0 || nums[mid] > nums[mid-1]) && (mid+1 == nums.length || nums[mid] > nums[mid+1]))
                return mid;

            if(nums[mid+1] > nums[mid]) {
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }

        return -1;
    }
}
```
