# Question

Given an unsorted integer array `nums`. Return _the smallest positive integer that is not present in `nums`._

## Leetcode Link

[41. First Missing Positive](https://leetcode.com/problems/first-missing-positive/)

## Approaches

1. **Boolean Array**: We can create a new boolean array seen and then go through the array and mark the elements that are present in the array. Then we can go through the boolean array and find the first element that is not present, if everything is present we return n+1. This has a time complexity of O(n) and space complexity of O(n).

2. **Index as a Hash Key**: Instead of creating a seperate boolean array, we can use the same array to mark the elements that are present. We can do this by marking the element at index i as negative if the element is present. Then we can go through the array and find the first element that is not present, if everything is present we return n+1. Note that since our solution will always be in the range [1, n+1], we can ignore the elements that are less than 1 or greater than n. This has a time complexity of O(n) and space complexity of O(1).

3. **Cycle Sort**: We can use the cycle sort algorithm to sort the array in place. Then we can go through the array and find the first element that is not present, if everything is present we return n+1. This has a time complexity of O(n) and space complexity of O(1).

## Solutions

### Java Approach 1

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        boolean[] seen = new boolean[n + 1]; // Array for lookup

        // Mark the elements from nums in the lookup array
        for (int num : nums) {
            if (num > 0 && num <= n) {
                seen[num] = true;
            }
        }

        // Iterate through integers 1 to n
        // return smallest missing positive integer
        for (int i = 1; i <= n; i++) {
            if (!seen[i]) {
                return i;
            }
        }

        // If seen contains all elements 1 to n
        // the smallest missing positive number is n + 1
        return n + 1;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;
        boolean doesOneExist = false;

        for(int i = 0; i < n; i++) {
            if(nums[i] == 1) doesOneExist = true;
            if(nums[i] <= 0 || nums[i] > n) nums[i] = 1;
        }

        if(!doesOneExist) return 1;

        for(int i = 0; i < n; i++) {
            int idx = Math.abs(nums[i]);
            if(nums[idx-1] > 0) nums[idx - 1] *= -1;
        }

        for(int i = 0; i < n; i++) {
            if(nums[i] > 0) return i + 1;
        }

        return n + 1;
    }
}
```

### Java Approach 3

```java
class Solution {
    public int firstMissingPositive(int[] nums) {
        int n = nums.length;

        // Use cycle sort to place positive elements smaller than n
        // at the correct index
        int i = 0;
        while (i < n) {
            int correctIdx = nums[i] - 1;
            if (nums[i] > 0 && nums[i] <= n && nums[i] != nums[correctIdx]) {
                swap(nums, i, correctIdx);
            } else {
                i++;
            }
        }

        // Iterate through nums
        // return smallest missing positive integer
        for (i = 0; i < n; i++) {
            if (nums[i] != i + 1) {
                return i + 1;
            }
        }

        // If all elements are at the correct index
        // the smallest missing positive number is n + 1
        return n + 1;
    }

    // Swaps two elements in nums
    private void swap(int[] nums, int index1, int index2) {
        int temp = nums[index1];
        nums[index1] = nums[index2];
        nums[index2] = temp;
    }
}
```
