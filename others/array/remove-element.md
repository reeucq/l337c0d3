# Question

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in nums **in-place**. The order of the elements may be changed. Then return _the number of elements in nums which are not equal to val._

## Leetcode Link

[27. Remove Element](https://leetcode.com/problems/remove-element/)

## Approaches

1. **Two Pointers**: The intuition behind this solution is to iterate through the array and keep track of two pointers: `j` and `i`. The `j` pointer represents the position where the next non-target element should be placed, while the `i` pointer iterates through the array elements. By overwriting the target elements with non-target elements, the solution effectively removes all occurrences of the target value from the array. The time complexity of this solution is $O(n)$ and space complexity is $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int j = 0;
        for(int num : nums) {
            if(num != val) nums[j++] = num;
        }
        return j;
    }
}
```
