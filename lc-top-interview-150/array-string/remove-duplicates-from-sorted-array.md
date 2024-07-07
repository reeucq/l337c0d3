# Question

Given an integer array `nums` sorted in **non-decreasing order**, remove the duplicates in-place such that each unique element appears only **once**. The **relative order** of the elements should be kept the **same**. Then return _the number of unique elements in **nums**_.

## Leetcode Link

[26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

## Approaches

1. **HashSet**: We will store the unique elements in a set and then iterate over the set to update the array. This method will take $O(n)$ time and $O(n)$ space.

2. **Two Pointers**: We will use two pointers, one for iterating over the array and the other for updating the array. This method will take $O(n)$ time and $O(1)$ space.

## Solutions

### Java Approach 1

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        Set<Integer> set = new HashSet<>();
        for (int num : nums) {
            set.add(num);
        }

        int i = 0;
        for (int num : set) {
            nums[i++] = num;
        }

        return set.size();
    }
}
```

### Java Approach 2

```java
class Solution {
    public int removeDuplicates(int[] nums) {
        int n = nums.length;
        int j = 1;

        for(int i = 0; i < n-1; i++) {
            if(nums[i] != nums[i+1]) {
                nums[j++] = nums[i+1];
            }
        }

        return j;
    }
}
```
