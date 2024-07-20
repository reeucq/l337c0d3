# Question

An array is **monotonic** if it is either monotone increasing or monotone decreasing. Given an integer array `nums`, return `true` _if the given array is monotonic, or `false` otherwise._

## Leetcode Link

[896. Monotonic Array](https://leetcode.com/problems/monotonic-array/)

## Approaches

1. **Two Pass**: This approach checks for increasing and decreasing monotonicity separately. time complexity is O(2n) and space complexity is O(1).

2. **One Pass**: This method checks for both increasing and decreasing monotonicity in a single pass. time complexity is O(n) and space complexity is O(1).

3. **And Operator**: This approach uses the `and` operator to check for increasing and decreasing monotonicity in a single pass. time complexity is O(n) and space complexity is O(1).

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        return isIncreasing(nums) || isDecreasing(nums);
    }

    private boolean isIncreasing(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] < nums[i - 1]) return false;
        }
        return true;
    }

    private boolean isDecreasing(int[] nums) {
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] > nums[i - 1]) return false;
        }
        return true;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean isMonotonic(int[] nums) {
        boolean inc = true, dec = true;

        for(int i = 1; i < nums.length; i++) {
            if(nums[i] > nums[i-1]) dec = false;
            if(nums[i] < nums[i-1]) inc = false;
            if(!inc && !dec) return false;
        }

        return true;
    }
}
```

### Java Approach 3

```java
public boolean isMonotonic(int[] A) {
    boolean inc = true, dec = true;
    for (int i = 1; i < A.length; ++i) {
        inc &= A[i - 1] <= A[i];
        dec &= A[i - 1] >= A[i];
    }
    return inc || dec;
}
```
