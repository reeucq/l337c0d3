# Question

Given a 2D integer array `matrix`, return* the **transpose** of `matrix`*.

## Leetcode Link

[867. Transpose Matrix](https://leetcode.com/problems/transpose-matrix/)

## Approach

1. **Brute Force**: Create a new matrix and fill it with the transpose of the given matrix. Time complexity is $O(n*m)$ and space complexity is $O(n*m)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[][] transpose(int[][] matrix) {
        int[][] result = new int[matrix[0].length][matrix.length];

        for(int i = 0; i < matrix.length; i++) {
            for(int j = 0; j < matrix[i].length; j++) {
                result[j][i] = matrix[i][j];
            }
        }

        return result;
    }
}
```
