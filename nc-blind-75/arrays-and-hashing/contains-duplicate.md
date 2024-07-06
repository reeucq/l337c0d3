# Question
Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

## Leetcode Link
[217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

## Approaches
1. **Brute Force**: We can use two nested loops to check if there are any duplicates in the array. This approach has a time complexity of $O(n^2)$ and a space complexity of $O(1)$.

2. **Sort**: We can sort the array and then check if any adjacant elements are equal. This approach has a time complexity of $O(n log n)$ and a space complexity of $O(1)$.

3. **HashSet**: We can use a HashSet to store the elements of the array. If we encounter an element that is already in the HashSet, we return `true`. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

4. **Functional Programming**: We can use the `distinct` method to get a stream of distinct elements and then compare the length of the original array with the length of the distinct stream. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

## Solutions
### Java Approach 3
```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> hs = new HashSet<>();
        for(int i = 0; i < nums.length; i++) {
            if(hs.contains(nums[i])) return true;
            hs.add(nums[i]);
        }
        return false;
    }
}
```

### Java Approach 4
```Java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        return 
        nums.length != Arrays.stream(nums).distinct().count();
    }
}
```

### JavaScript Approach 4
```JavaScript
var containsDuplicate = function(nums) {
    return nums.length !== new Set(nums).size()
};
```

### Python Approach 4
```Python
def containsDuplicate(nums):
    return len(nums) != len(set(nums))
```