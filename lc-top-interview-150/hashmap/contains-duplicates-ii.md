# Question

Given an integer array `nums` and an integer `k`, return `true` _if there are two **distinct indices**_ `i` and `j` in the array such that `nums[i] == nums[j]` and `abs(i - j) <= k`.

## Leetcode Link

[219. Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii)

## Approaches

1. **Brute Force**: We can use two nested loops to check if there are any duplicates in the array with a difference of at most `k`. This approach has a time complexity of $O(n^2)$ and a space complexity of $O(1)$.

2. **HashMap**: We can use a HashMap to store the elements of the array along with their indices. If we encounter an element that is already in the HashMap and the difference between the current index and the previous index is at most `k`, we return `true`. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

3. **Sliding Window**: We can use a sliding window of size `k` to check for duplicates. We add elements to the window and remove elements that are outside the window. This approach has a time complexity of $O(n)$ and a space complexity of $O(k)$.

## Solutions

### Java Approach 1

```Java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        for(int i = 0; i < nums.length; i++) {
            for(int j = i+1; j < nums.length; j++) {
                if(nums[i] == nums[j] && Math.abs(i-j) <= k) return true;
            }
        }
        return false;
    }
}
```

### Java Approach 2

```Java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Map<Integer,Integer> hm = new HashMap<>();

        for(int i = 0; i < nums.length; i++) {
            if(hm.containsKey(nums[i])) {
                int prevIdx = hm.get(nums[i]);
                if(i - prevIdx <= k) return true;
            }
            hm.put(nums[i],i);
        }
        return false;
    }
}
```

### Java Approach 3

```Java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        if(k == 0) return false;
        HashSet<Integer> sw = new HashSet<>();

        for(int i = 0; i < nums.length; i++) {
            if(sw.contains(nums[i])) return true;
            if(i >= k) sw.remove(nums[i - k]);
            sw.add(nums[i]);
        }

        return false;
    }
}
```
