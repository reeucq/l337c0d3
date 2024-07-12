# Question

A **permutation** of an array of integers is an arrangement of its members into a sequence or linear order.

- For example, for `arr = [1,2,3]`, the following are all the permutations of arr: `[1,2,3], [1,3,2], [2, 1, 3], [2, 3, 1], [3,1,2], [3,2,1]`.

The **next permutation** of an array of integers is the next lexicographically greater permutation of its integer. More formally, if all the permutations of the array are sorted in one container according to their lexicographical order, then the **next permutation** of that array is the permutation that follows it in the sorted container. If such arrangement is not possible, the array must be rearranged as the lowest possible order (i.e., sorted in ascending order).

- For example, the **next permutation** of `arr = [1,2,3] is [1,3,2].`
- Similarly, the **next permutation** of `arr = [2,3,1] is [3,1,2].`

Given an array of integers `nums`, _find the next permutation of `nums`._

## Leetcode Link

[31. Next Permutation](https://leetcode.com/problems/next-permutation/)

## Approaches

- **Brute Force**: In this we generate all the permutations of the array and then sort them and then find the next permutation. This approach is not efficient as it has a time complexity of $O(n! * n)$ and space complexity of $O(n)$.

- **Optimal Appraoch**: In this approach we find the next permutation in a single pass. We start from the end of the array and find the first element which is not in increasing order. We then find the next greater element than this element and swap them. Then we reverse the array from the next element of the element we swapped till the end of the array. This approach has a time complexity of $O(n)$ and space complexity of $O(1)$. [Read More](https://en.wikipedia.org/wiki/Permutation#Generation_in_lexicographic_order)

## Solutions

### Java Approach 2

```java
class Solution {
    public void nextPermutation(int[] nums) {
        int n = nums.length;
        // find the breakpoint
        int breakpoint = -1;
        for(int i = n-2; i >=0; i--) {
            if(nums[i] < nums[i+1]) {
                breakpoint = i;
                break;
            }
        }

        if(breakpoint == -1) {
            reverse(nums,0,n-1);
            return;
        }

        // find the replacement and swap breakpoint and replacement
        int replacement = -1;
        for(int i = n-1; i >= breakpoint; i--) {
            if(nums[i] > nums[breakpoint]) {
                int temp = nums[breakpoint];
                nums[breakpoint] = nums[i];
                nums[i] = temp;
                break;
            }
        }

        // sort the array after the breakpoint in ascending order
        reverse(nums,breakpoint+1,n-1);
        return;
    }

    private void reverse(int[] nums, int start, int end) {
        while(start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```
