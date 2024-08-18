# Question

Given an array of integers `nums`, sort the array in ascending order and return it.

## Leetcode Link

[912. Sort an Array](https://leetcode.com/problems/sort-an-array/)

## Approach

1. **Merge Sort**: This algorithm sorts an array using the merge sort technique. It divides the array into two halves, sorts each half recursively, and merges the sorted halves. The merge operation combines two sorted arrays into a single sorted array. The algorithm uses a helper function to merge two arrays, and the main function recursively sorts the array by dividing it into smaller subarrays.

2. **Quick Sort**: This algorithm sorts an array using the quick sort technique. It selects a pivot element, partitions the array into two subarrays based on the pivot, and recursively sorts the subarrays. The partition operation rearranges the elements such that all elements less than the pivot are on the left, and all elements greater than the pivot are on the right. The algorithm uses a helper function to partition the array and the main function to sort the array recursively.

## Solutions

### Merge Sort

```java
class Solution {
    public int[] sortArray(int[] nums) {
        mergeSort(nums, 0, nums.length - 1);
        return nums;
    }

    private static void mergeSort(int[] nums, int low, int high) {
        if(low < high) {
            int mid = (int) Math.floor((low+high)/2);
            mergeSort(nums,low,mid);
            mergeSort(nums,mid+1,high);
            merge(nums,low,mid,high);
        }
    }

    private static void merge(int[] nums, int low, int mid, int high) {
        int[] b = new int[high - low + 1];
        int i = low, j  = mid + 1, k = 0;

        while(i <= mid && j <= high) {
            if(nums[i] < nums[j]) {
                b[k++] = nums[i++];
            } else {
                b[k++] = nums[j++];
            }
        }

        while(i <= mid) {
            b[k++] = nums[i++];
        }

        while(j <= high) {
            b[k++] = nums[j++];
        }

        System.arraycopy(b, 0, nums, low, b.length);
    }
}
```

### Quick Sort

```java
import java.util.Random;

class Solution {
    private static final Random rand = new Random();

    public int[] sortArray(int[] nums) {
        quickSort(nums, 0, nums.length - 1);
        return nums;
    }

    private static void quickSort(int[] nums, int low, int high) {
        if (low < high) {
            int pivot = partition(nums, low, high);
            quickSort(nums, low, pivot - 1);
            quickSort(nums, pivot + 1, high);
        }
    }

    private static int partition(int[] nums, int low, int high) {
        // Select a random pivot and swap with the first element
        int pivotIndex = low + rand.nextInt(high - low + 1);
        swap(nums, low, pivotIndex);

        int pivotElement = nums[low];
        int j = low;

        for (int i = low + 1; i <= high; i++) {
            if (nums[i] < pivotElement) {
                j++;
                if (i != j) {
                    swap(nums, i, j);
                }
            }
        }

        int pivotPoint = j;
        swap(nums, low, pivotPoint);

        return pivotPoint;
    }

    private static void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
}

```
