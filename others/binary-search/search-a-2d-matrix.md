# Question

You are given an `m x n` integer matrix `matrix` with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return _`true` if `target` is in `matrix` or `false` otherwise._

## Leetcode Link

[74. Search a 2D Matrix](https://leetcode.com/problems/search-a-2d-matrix/)

## Intuition

This solution implements an efficient search in a sorted 2D matrix. It first checks if the target is within the matrix's range. Then, it performs a binary search on the first column to find the potential row containing the target. Finally, it conducts another binary search within that row to locate the target. If found, it returns true; otherwise, it returns false. This approach has a time complexity of O(log(n) + log(m)), where n is the number of rows and m is the number of columns.

## Solution

### Java

```java
class Solution {
    public boolean searchMatrix(int[][] matrix, int target) {
        int n = matrix.length;
        int m = matrix[0].length;

        // Check if target is smaller than the smallest element
        if (target < matrix[0][0]) return false;

        // Check if target is larger than the largest element
        if (target > matrix[n-1][m-1]) return false;

        // search the row which might have the target
        int top = 0;
        int bottom = n - 1;

        while (top <= bottom) {
            int mid = top + (bottom - top) / 2;
            if (matrix[mid][0] == target) return true;
            else if (matrix[mid][0] > target) bottom = mid - 1;
            else top = mid + 1;
        }

        // At this point, 'bottom' is the index of the row where the target could be
        int row = bottom;
        int left = 0;
        int right = m - 1;

        // search the column which might contain the target
        while (left <= right) {
            int mid = left + (right - left) / 2;
            if (matrix[row][mid] == target) return true;
            else if (matrix[row][mid] > target) right = mid - 1;
            else left = mid + 1;
        }

        return false;
    }
}
```
