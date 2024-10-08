# Question

Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.
You may assume that each input would have **exactly one solution**, and you may not use the same element twice.
You can return the answer in any order.

## Leetcode Link

[1. Two Sum](https://leetcode.com/problems/two-sum/)

## Approaches

1. **Brute Force**: This can be done using nested loops, where the outer loop iterates from the first element to the second-to-last element, and the inner loop iterates from the next element to the last element. However, this approach has a time complexity of $O(n^2)$. Space complexity is $O(1)$.

2. **HashMap**: A more efficient approach is to use a hash table (unordered_map in C++). We can iterate through the array once, and for each element, check if the target minus the current element exists in the hash table. If it does, we have found a valid pair of numbers. If not, we add the current element to the hash table. Time complexity of this approach is $O(n)$ and Space complexity is $O(n)$.

3. **Greedy - Two Pointers**: In this we'll first sort the array and then use two pointers to find the pair. This approach has a time complexity of $O(n\log n)$ and space complexity of $O(1)$. However, this approach is not suitable for this problem as we need to return the indices of the elements, and sorting the array will change the indices, It's only application when we're asked to find whether the pair exists or not.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int n = nums.length;
        for (int i = 0; i < n - 1; i++) {
            for (int j = i + 1; j < n; j++) {
                if (nums[i] + nums[j] == target) {
                    return new int[]{i, j};
                }
            }
        }
        return new int[]{}; // No solution found
    }
}
```

### Java Approach 2

```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> numMap = new HashMap<>();
        int n = nums.length;

        for (int i = 0; i < n; i++) {
            int complement = target - nums[i];
            if (numMap.containsKey(complement)) {
                return new int[]{numMap.get(complement), i};
            }
            numMap.put(nums[i], i);
        }

        return new int[]{}; // No solution found
    }
}
```

### Java Approach 1

```java
public static String twoSum(int n, int []arr, int target) {
    Arrays.sort(arr);
    int left = 0, right = n - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) {
            return "YES";
        } else if (sum < target) left++;
        else right--;
    }
    return "NO";
}
```
