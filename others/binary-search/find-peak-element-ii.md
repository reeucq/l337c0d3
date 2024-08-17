# Question

A **peak** element in a 2D grid is an element that is **strictly greater** than all of its **adjacent** neighbors to the left, right, top, and bottom.

Given a **0-indexed** `m x n` matrix `mat` where **no two adjacent cells are equal**, find **any** peak element `mat[i][j]` and return _the length 2 array [i,j]._

## Leetcode Link

[1901. Find Peak Element II](https://leetcode.com/problems/find-a-peak-element-ii/)

## Intuition

- The algorithm uses binary search on the columns of the matrix to find a peak element.
- For each middle column, it finds the maximum element and its row index.
- It then compares this element with its left and right neighbors (if they exist).
- If a neighbor is greater, it adjusts the search range accordingly; otherwise, it returns the current position as the peak.
- This process continues until a peak is found or the search range is exhausted.

## Solutions

### Java

```java
class Solution {
    public int[] findPeakGrid(int[][] mat) {
        int n = mat.length;
        int m = mat[0].length;
        int l = 0, r = m - 1;

        while(l <= r) {
            int j = (l + r) / 2;

            int max = 0;
            int i = 0;
            for(int k = 0; k < n; k++) {
                if(mat[k][j] > max) {
                    max = mat[k][j];
                    i = k;
                }
            }

            if((j-1) >= 0 && mat[i][j-1] > mat[i][j]) {
                r = j - 1;
            } else if((j+1) < m && mat[i][j+1] > mat[i][j]) {
                l = j + 1;
            } else {
                return new int[]{i,j};
            }
        }

        return new int[]{-1,-1};
    }
}
```
