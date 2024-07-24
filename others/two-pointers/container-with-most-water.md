# Question

You are given an integer array `height` of length `n`. There are `n` vertical lines drawn such that the two endpoints of the `ith` line are `(i, 0)` and `(i, height[i])`.

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return _the maximum amount of water a container can store._

## Leetcode Link

[11. Container With Most Water](https://leetcode.com/problems/container-with-most-water/)

## Approaches

1. **Brute Force**: We can use two nested loops to find the maximum area. The time complexity of this approach is $O(n^2)$

2. **Two Pointers - Greedy**: Initialize two pointers, one at the start of the array (left) and one at the end (right). Calculate the area between these two lines and keep track of the maximum area seen so far. Move the pointer that points to the shorter line inward. Repeat until both pointers meet. The intuition behind moving the shorter line is that the area is limited by the shorter line. Moving the taller line inward would only decrease the width without any possibility of increasing the height. This has a time complexity of $O(n)$

## Solutions

### Java Approach 1

```java
public static int maxArea(int[] height) {
    int maxArea = 0;
    int n = height.length;

    for (int i = 0; i < n - 1; i++) {
        for (int j = i + 1; j < n; j++) {
            // Calculate width
            int width = j - i;

            // Calculate height (the minimum of the two lines)
            int h = Math.min(height[i], height[j]);

            // Calculate area
            int area = width * h;

            // Update maxArea if necessary
            maxArea = Math.max(maxArea, area);
        }
    }

    return maxArea;
}
```

### Java Approach 2

```java
public class ContainerWithMostWaterBruteForce {
    public static int maxArea(int[] height) {
        int maxArea = 0;
        int n = height.length;

        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                // Calculate width
                int width = j - i;

                // Calculate height (the minimum of the two lines)
                int h = Math.min(height[i], height[j]);

                // Calculate area
                int area = width * h;

                // Update maxArea if necessary
                maxArea = Math.max(maxArea, area);
            }
        }

        return maxArea;
    }
```
