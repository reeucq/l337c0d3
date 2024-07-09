# Question

You are given two integer arrays `nums1` and `nums2`, sorted in **non-decreasing order**, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively.

**Merge** `nums1` and `nums2` into a single array sorted in **non-decreasing order**.

The final sorted array should not be returned by the function, but instead be _stored inside the array_ `nums1`. To accommodate this, `nums1` has a length of `m + n`, where the first `m` elements denote the elements that should be merged, and the last `n` elements are set to `0` and should be ignored. `nums2` has a length of `n`.

## Leetcode Link

[88. Merge Sorted Array](https://leetcode.com/problems/merge-sorted-array/)

## Approaches

1. **Two Pointers (Start from the End)**: We can start from the end of both arrays and compare the elements. We can then place the larger element at the end of the `nums1` array. This approach has a time complexity of $O(n + m)$ and a space complexity of $O(1)$.

2. **Using Extra Space**: We can create a copy of the `nums1` array and then merge the two arrays using two pointers. This approach has a time complexity of $O(n + m)$ and a space complexity of $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = m-1;
        int j = n-1;
        int k = m + n - 1;

        while(j >= 0) {
            if(i >= 0 && nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
    }
}
```

### Java Approach 2

```java
class Solution {
    public void merge(int[] nums1, int m, int[] nums2, int n) {
        int i = 0;
        int j = 0;
        int k = 0;

        int[] nums3 = new int[nums1.length];
        System.arraycopy(nums1,0,nums3,0,m);

        while(i < m && j < n) {
            if(nums3[i] < nums2[j]) {
                nums1[k++] = nums3[i];
                i++;
            } else {
                nums1[k++] = nums2[j];
                j++;
            }
        }

        while(i < m) {
            nums1[k++] = nums3[i];
            i++;
        }

        while(j < n) {
            nums1[k++] = nums2[j];
            j++;
        }
    }
}
```
