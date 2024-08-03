# Question

Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.

## Leetcode Link

[42. Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)

## Approaches

1. **Using Extra Space**: We can store the maximum height of the bars to the left and right of each bar in two separate arrays. Then, for each bar, the amount of water it can trap is `min(left_max, right_max) - height[i]`. The total amount of water trapped is the sum of the amount of water trapped by each bar. This approach requires `O(n)` extra space.

2. **Two Pointers**: We can use two pointers to keep track of the maximum height of the bars to the left and right of each bar. We can then calculate the amount of water trapped by each bar using the same formula as above. This approach requires `O(1)` extra space.

3. **Stack Based Approach**: We can use a stack to keep track of the indices of the bars. If the current bar is higher than the bar at the top of the stack, we can calculate the amount of water trapped by the bar at the top of the stack and add it to the total amount of water trapped. This approach requires `O(n)` extra space.

## Solutions

### Java Approach 1

```java
class Solution {
    public int trap(int[] height) {
        int[] maxLeft = new int[height.length];
        int[] maxRight = new int[height.length];

        maxLeft[0] = height[0];
        for(int i = 1; i < height.length; i++) {
            maxLeft[i] = Math.max(maxLeft[i-1],height[i]);
        }

        maxRight[height.length - 1] = height[height.length - 1];
        for(int i = height.length - 2; i >= 0; i--) {
            maxRight[i] = Math.max(maxRight[i+1],height[i]);
        }

        int water = 0;
        for(int i = 0; i < height.length; i++) {
            water += Math.min(maxLeft[i],maxRight[i]) - height[i];
        }

        return water;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int trap(int[] height) {
        if (height == null || height.length < 3) {
            return 0;
        }

        int left = 0, right = height.length - 1;
        int leftMax = 0, rightMax = 0;
        int water = 0;

        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= leftMax) {
                    leftMax = height[left];
                } else {
                    water += leftMax - height[left];
                }
                left++;
            } else {
                if (height[right] >= rightMax) {
                    rightMax = height[right];
                } else {
                    water += rightMax - height[right];
                }
                right--;
            }
        }

        return water;
    }
}
```

### Java Approach 3

```java
class Solution {
    public int trap(int[] height) {
        if (height == null || height.length < 3) {
            return 0;
        }

        int water = 0;
        Stack<Integer> stack = new Stack<>();

        for (int i = 0; i < height.length; i++) {
            while (!stack.isEmpty() && height[i] > height[stack.peek()]) {
                int top = stack.pop();

                if (stack.isEmpty()) {
                    break;
                }

                int distance = i - stack.peek() - 1;
                int boundedHeight = Math.min(height[i], height[stack.peek()]) - height[top];
                water += distance * boundedHeight;
            }
            stack.push(i);
        }

        return water;
    }
}
```
