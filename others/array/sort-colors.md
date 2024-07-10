# Question

Given an array `nums` with `n` objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.

## Leetcode Link

[75. Sort Colors](https://leetcode.com/problems/sort-colors/)

## Approaches

1. **Bucket Sort**: Count the number of 0s, 1s and 2s and then fill the array with the count of 0s, 1s and 2s. This has a time complexity of $O(n)$ and space complexity of $O(1)$.

2. **Dutch National Flag Algorithm**: This is a three-way partitioning algorithm which is used to sort an array of 0s, 1s and 2s. This algorithm is designed by Edsger Dijkstra. This has a time complexity of $O(n)$ and space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public void sortColors(int[] nums) {
        int count0 = 0;
        int count1 = 0;
        int count2 = 0;

        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0) count0++;
            else if(nums[i] == 1) count1++;
            else count2++;
        }

        int k = 0;
        while(count0 != 0) {
            nums[k++] = 0;
            count0--;
        }

        while(count1 != 0) {
            nums[k++] = 1;
            count1--;
        }

        while(count2 != 0) {
            nums[k++] = 2;
            count2--;
        }
    }
}
```

### Java Approach 2

```java
class Solution {
    public void sortColors(int[] nums) {
        int mid = 0;
        int low = 0;
        int high = nums.length - 1;

        while(mid <= high) {
            if(nums[mid] == 0) {
                int temp = nums[mid];
                nums[mid] = nums[low];
                nums[low] = temp;
                low++; mid++;
            } else if(nums[mid] == 1) {
                mid++;
            } else {
                int temp = nums[high];
                nums[high] = nums[mid];
                nums[mid] = temp;
                high--;
            }
        }
    }
}
```
