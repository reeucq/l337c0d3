# Question

You are given an `n x n` 2D `matrix` representing an image, rotate the image by **90** degrees (clockwise).

You have to rotate the image in-place, which means you have to modify the input 2D matrix directly. **DO NOT** allocate another 2D matrix and do the rotation.

## Leetcode Link

[48. Rotate Image](https://leetcode.com/problems/rotate-image/)

## Approaches

1. **Transpose & Reverse Row**: To rotate the image by 90 degrees, we can first transpose the matrix and then reverse each row. This will rotate the image by 90 degrees clockwise. The time complexity of this approach is $O(n^2)$ and the space complexity is $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public void rotate(int[][] matrix) {
        int n = matrix.length;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int temp = matrix[i][j];
                matrix[i][j] = matrix[j][i];
                matrix[j][i] = temp;
            }
        }

        for(int i = 0; i < n; i++) {
            reverseRow(matrix[i],0,n-1);
        }
    }

    private void reverseRow(int[] row,int begin,int end) {
        while(begin < end) {
            int temp = row[begin];
            row[begin] = row[end];
            row[end] = temp;
            begin++;
            end--;
        }
    }
}
```

## Notes

### Rotate by +90 degrees (clockwise)

1. Transpose the matrix
2. Reverse each row

### Rotate by -90 degrees (anti-clockwise)

#### Method 1

1. Transpose the matrix
2. Reverse each column

#### Method 2

1. Reverse each row
2. Transpose the matrix

### Rotate by +180 degrees (clockwise)

#### Method 1

1. Rotate by +90 degrees twice

#### Method 2

1. Reverse each row and then reverse each column

### Rotate by -180 degrees (anti-clockwise)

#### Method 1

1. Rotate by -90 degrees twice

#### Method 2

1. Reverse each column and then reverse each row

#### Method 3

1. Rotate by +180 degrees as they are the same

[Read More](https://stackoverflow.com/questions/42519/how-do-you-rotate-a-two-dimensional-array)
