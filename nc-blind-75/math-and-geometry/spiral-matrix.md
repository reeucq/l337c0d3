# Question

Given an `m x n` `matrix`, return all elements of the `matrix` in spiral order.

## Leetcode Link

[54. Spiral Matrix](https://leetcode.com/problems/spiral-matrix/)

## Approaches

1. **Simulation**: Keep track of the boundaries of the matrix and simulate the spiral order traversal. Time complexity: $O(m \times n)$, Space complexity: $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> res = new ArrayList<>();
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return res;
        }

        int m = matrix.length, n = matrix[0].length;
        int top = 0, left = 0, bottom = m - 1, right = n - 1;

        while (top <= bottom && left <= right) {
            // Traverse right
            for (int i = left; i <= right; i++) {
                res.add(matrix[top][i]);
            }
            top++;

            // Traverse down
            for (int i = top; i <= bottom; i++) {
                res.add(matrix[i][right]);
            }
            right--;

            if (top <= bottom) {
                // Traverse left
                for (int i = right; i >= left; i--) {
                    res.add(matrix[bottom][i]);
                }
                bottom--;
            }

            if (left <= right) {
                // Traverse up
                for (int i = bottom; i >= top; i--) {
                    res.add(matrix[i][left]);
                }
                left++;
            }
        }

        return res;
    }
}
```

### Note

_if you don't want those extra ifs, then you can change the while condition to res.size() <= m\*n_
