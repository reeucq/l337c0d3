# Question

Given an array `nums` of size `n`, return the majority element.

The majority element is the element that appears more than `⌊n / 2⌋` times. You may assume that the majority element always exists in the array.

## Leetcode Link

[169. Majority Element](https://leetcode.com/problems/majority-element/)

## Approaches

1. **Sorting**: The intuition behind this approach is that if an element occurs more than n/2 times in the array (where n is the size of the array), it will always occupy the middle position when the array is sorted. Therefore, we can sort the array and return the element at index `n/2`. This approach has a time complexity of O(nlogn) due to the sorting operation.

2. **Hash Map**: The intuition behind this approach is to count the frequency of each element in the array using a hash map. We can iterate through the array and keep track of the count of each element. If the count of an element becomes greater than n/2, we return that element as the majority element. This approach has a time complexity of O(n) and a space complexity of O(n) due to the hash map.

3. **Boyer-Moore Voting Algorithm**: The Boyer-Moore Voting Algorithm is an efficient algorithm to find the majority element in an array. The algorithm works by maintaining a candidate element and a count. Initially, the candidate element is set to the first element of the array, and the count is set to 1. We then iterate through the array, and for each element, we check if it is equal to the candidate element. If it is, we increment the count; otherwise, we decrement the count. If the count becomes 0, we update the candidate element to the current element and set the count to 1. At the end of the iteration, the candidate element will be the majority element. This approach has a time complexity of O(n) and a space complexity of O(1).

## Solutions

### Java Approach 1

```java
class Solution {
    public int majorityElement(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        return nums[n/2];
    }
}
```

### Java Approach 2

```java
class Solution {
    public int majorityElement(int[] nums) {
        HashMap<Integer,Integer> hm = new HashMap<>();
        for(int num : nums) hm.put(num,hm.getOrDefault(num,0)+1);
        for(Map.Entry<Integer,Integer> entry : hm.entrySet())
            if(entry.getValue() > nums.length/2) return entry.getKey();
        return -1;
    }
}
```

### Java Approach 3

```java
class Solution {
    public int majorityElement(int[] nums) {
        int candidate = nums[0];
        int count = 1;

        for (int i = 1; i < nums.length; i++) {
            if (count == 0) {
                candidate = nums[i];
                count = 1;
            } else if (candidate == nums[i]) {
                count++;
            } else {
                count--;
            }
        }

        return candidate;
    }
}
```
