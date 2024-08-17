# Question

You are given a **0-indexed** array `mountain`. Your task is to find all the **peaks** in the `mountain` array.

Return _an array that consists of indices of **peaks** in the given array in **any order**._

## Leetcode Link

[2951. Find the Peaks](https://leetcode.com/problems/find-the-peaks/)

## Intuition

- The algorithm uses a linear scan to find all the peaks in the given array.
- It iterates over the array and checks if the current element is greater than its neighbors.
- If the current element is greater than both its left and right neighbors, it is a peak.
- The algorithm adds the index of the peak to the result array.
- The algorithm returns the result array containing the indices of all the peaks in the given array.

## Solution

```java
class Solution {
    public List<Integer> findPeaks(int[] mountain) {
        ArrayList<Integer> res = new ArrayList<>();
        for(int i = 1; i < mountain.length - 1; i++) {
            if(mountain[i-1] < mountain[i] && mountain[i] > mountain[i+1]) {
                res.add(i);
            }
        }
        return res;
    }
}
```
