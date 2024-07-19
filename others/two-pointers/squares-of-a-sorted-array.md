# Question

Given an integer array `nums` sorted in non-decreasing order, return _an array of the squares of each number sorted in non-decreasing order._

## Leetcode Link

[977. Squares of a Sorted Array](https://leetcode.com/problems/squares-of-a-sorted-array/)

## Approaches

1. **Sorting**: We can square each element of the array and then sort the array. This approach has a time complexity of O(nlogn) and space complexity of O(n).

2. **Two Pointers**: We can use two pointers to solve this problem. We place the left pointer on the start of the array and right pointer at the end, then compare the squares of the elements at these pointers. We place the larger square at the end of the result array and move the pointer accordingly. This approach has a time complexity of O(n) and space complexity of O(n).

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        for(int i=0;i<n;i++) {
            res[i] = nums[i] * nums[i];
        }
        Arrays.sort(res);
        return res;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int[] sortedSquares(int[] nums) {
        int[] res = new int[nums.length];

        int l = 0;
        int r = nums.length - 1;
        int k = nums.length - 1;

        while(l <= r) {
            int lSq = nums[l] * nums[l];
            int rSq = nums[r] * nums[r];

            if(lSq > rSq) {
                res[k--] = lSq;
                l++;
            } else {
                res[k--] = rSq;
                r--;
            }
        }

        return res;
    }
}
```
