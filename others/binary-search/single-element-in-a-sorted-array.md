# Question

You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.

Return _the single element that appears only once._

## Leetcode Link

[540. Single Element in a Sorted Array](https://leetcode.com/problems/single-element-in-a-sorted-array/)

## Approaches

1. **Binary Search**: We'll first check if the middle element is the only element remaining in our search space or if it is not equal to its neighbors, if that's the case, we've found the answer, otw we'll trim down our search space. The key to trim down our search space works as follows - we know there will always be odd no. of elements in the array, so after checking the middle element and determining the size of the remaining portions, we'll move our search space towards the portion whose no. of elements are odd. This way we'll keep on reducing our search space until we find the single element. This will take `O(log n)` time.

## Solutions

### Java Approach 1

```java
class Solution {
    public int singleNonDuplicate(int[] nums) {
        int l = 0;
        int r = nums.length - 1;

        while(l <= r) {
            int m = l + (r-l)/2;

            // first we'll check if mid is not equal to its neighbors of if its the only element left
            // if yes, we'll j return it since that's our answer
            if((m - 1 < 0 || nums[m-1] != nums[m]) && (m + 1 == nums.length || nums[m+1] != nums[m]))
                return nums[m];

            // now since mid is equal to one of its neighbor
            // we'll check the size of one of the side and determine if its odd
            // if its odd, we'll search that side, since that's gonna contain the single element
            // otw we'll look at the other side
            // and trim our search space accordingly
            int leftSize = 0;
            leftSize = (nums[m-1] == nums[m]) ? m - 1 : m;

            if(leftSize % 2 == 1) r = m - 1;
            else l = m + 1;
        }

        return -1;
    }
}
```
