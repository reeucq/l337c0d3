# Question

Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.

## Leetcode Link

[189. Rotate Array](https://leetcode.com/problems/rotate-array/)

## Approaches

1. **Using ArrayList**: We can use an ArrayList to store the elements of the array. We can then shift the elements of the ArrayList by `k` positions to the right. Finally, we can copy the elements of the ArrayList back to the original array. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

2. **In Place Modification using Indexes**: We can store the elements that we have to move to first in a temporary array, then shift the elements to the right by `k` positions, and finally copy the elements from the temporary array to the original array. This approach has a time complexity of $O(n)$ and a space complexity of $O(k)$.

3. **Using Reverse**: We can reverse the entire array. Then, we can reverse the first `k` elements and the remaining `n-k` elements separately. Finally, we can reverse the entire array to get the desired result. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public void rotate(int[] nums, int k) {
        int n = nums.length;
        if(n == 1) return;
        if(k == 0) return;
        if(k > n) k = k % n;
        ArrayList<Integer> l = new ArrayList<>();
        for(int i = (n-k); i < n; i++) l.add(nums[i]);
        for(int i = 0; i < (n-k); i++) l.add(nums[i]);
        for(int i = 0; i < l.size(); i++) nums[i] = l.get(i);
    }
}
```

### Java Approach 2

```java
class Solution {
    public void rotate(int[] nums, int k) {
        if(nums.length == 1) return;
        if(k == 0) return;
        if(k > nums.length) k = k % nums.length;

        int[] temp = new int[k];

        for(int i = 0; i < k; i++) temp[i] = nums[nums.length-k+i];
        for(int i = nums.length-1; i >= k; i--) nums[i] = nums[i-k];
        for(int i = 0; i < k; i++) nums[i] = temp[i];
    }
}
```

### Java Approach 3

```java
class Solution {
    public void rotate(int[] nums, int k) {
        k %= nums.length;
        reverse(nums, 0, nums.length - 1);
        reverse(nums, 0, k - 1);
        reverse(nums, k, nums.length - 1);
    }

    public void reverse(int[] nums, int start, int end) {
        while (start < end) {
            int temp = nums[start];
            nums[start] = nums[end];
            nums[end] = temp;
            start++;
            end--;
        }
    }
}
```
