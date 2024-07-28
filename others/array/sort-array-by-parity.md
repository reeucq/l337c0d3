# Question

Given an integer array `nums`, move all the even integers at the beginning of the array followed by all the odd integers.

## Leetcode Link

[905. Sort Array By Parity](https://leetcode.com/problems/sort-array-by-parity/)

## Approaches

1. **Using Extra Memory**: We can create a resultant array and then pass through the input array. If the element is even, we can add it to the front of the resultant array; otherwise, we can add it to the end. This approach has a time complexity of `O(n)` and a space complexity of `O(n)`.

2. **Two Pointer - In Place**: We can use two pointers, `i` and `j` to iterate through the array. We can move `i` from the start of the array and `j` from the end of the array. If `nums[i]` is odd and `nums[j]` is even, we can swap the elements. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] sortArrayByParity(int[] nums) {
        int[] res = new int[nums.length];
        int l = 0, r = nums.length - 1;
        for(int num : nums) {
            if(num % 2 == 0) res[l++] = num;
            else res[r--] = num;
        }
        return res;
    }
}
```

### Java Approach 2

```java
public int[] sortArrayByParity(int[] A) {
    int i = 0;
    int j = A.length - 1;
    while (i < j) {
        if(A[i] % 2 == 0) {
            // Even first
            i++;
        }
        else {
            if(A[j] % 2 != 0) {
                // Both odd
                j--;
            }
            if (A[j] % 2 == 0) {
                // Odd, Even
                swap(A, i, j);
                i++;
                j--;
            }
        }
    }


    return A;
}

private void swap(int[] nums, int i, int j) {
    int temp = nums[i];
    nums[i] = nums[j];
    nums[j] = temp;
}
```
