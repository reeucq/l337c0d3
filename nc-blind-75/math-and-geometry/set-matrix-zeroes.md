# Question

Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`'s.
You must do it **in place**.

## Leetcode Link

[73. Set Matrix Zeroes](https://leetcode.com/problems/set-matrix-zeroes/)

## Approaches

1. **Using Extra Space**: We can use an extra matrix to store the information about the rows and columns that need to be set to zero. We can then iterate over the matrix and set the rows and columns to zero based on the information stored in the extra matrix. This approach requires `O(m + n)` extra space. The time complexity of this approach is `O(m * n)`.

2. **Using Constant Space**: We can use the first row and first column of the matrix to store the information about the rows and columns that need to be set to zero. We can then iterate over the matrix and set the rows and columns to zero based on the information stored in the first row and first column. This approach requires constant extra space. The time complexity of this approach is `O(m * n)`.

## Solutions

### Java Approach 1

```java
class Solution {
   public void setZeroes(int[][] matrix) {
       int m = matrix.length;
       int n = matrix[0].length;
       boolean[] rows = new boolean[m];
       boolean[] cols = new boolean[n];

       for(int i = 0; i < m; i++) {
           for(int j = 0; j < n; j++) {
               if(matrix[i][j] == 0) {
                   rows[i] = true;
                   cols[j] = true;
               }
           }
       }

       for(int i = 0; i < m; i++) {
           for(int j = 0; j < n; j++) {
               if(rows[i] || cols[j]) {
                   matrix[i][j] = 0;
               }
           }
       }
   }
}
```

### Java Approach 2

```java
public class Solution {
public void setZeroes(int[][] matrix) {
    boolean fr = false,fc = false;
    for(int i = 0; i < matrix.length; i++) {
        for(int j = 0; j < matrix[0].length; j++) {
            if(matrix[i][j] == 0) {
                if(i == 0) fr = true;
                if(j == 0) fc = true;
                matrix[0][j] = 0;
                matrix[i][0] = 0;
            }
        }
    }
    for(int i = 1; i < matrix.length; i++) {
        for(int j = 1; j < matrix[0].length; j++) {
            if(matrix[i][0] == 0 || matrix[0][j] == 0) {
                matrix[i][j] = 0;
            }
        }
    }
    if(fr) {
        for(int j = 0; j < matrix[0].length; j++) {
            matrix[0][j] = 0;
        }
    }
    if(fc) {
        for(int i = 0; i < matrix.length; i++) {
            matrix[i][0] = 0;
        }
    }

}
```
