# Question

Given a **non-empty** array of integers `nums`, every element appears twice except for one. Find that single one.
You must implement a solution with a linear runtime complexity and use only constant extra space.

## Leetcode Link

[136. Single Number](https://leetcode.com/problems/single-number/)

## Approaches

1. **Bit Manipulation**: If we take XOR of zero and some bit, it will return that bit. If we take XOR of two same bits, it will return 0. So we can XOR all bits together to find the unique number, since we know that all numbers except one appear twice. It'll take $O(n)$ time and $O(1)$ space.

2. **HashSet**: We can use a hashset to store the numbers. If the number is already in the set, we remove it. The remaining number will be the unique number. It'll take $O(n)$ time and $O(n)$ space.

3. **Sorting**: We can sort the array and then check the adjacent elements. If the adjacent elements are not equal, then the current element is the unique number. It'll take $O(n\log n)$ time and $O(1)$ space.

## Solutions

### Java Approach 1

```java
class Solution {
    public int singleNumber(int[] nums) {
        int ans = 0;
        for(int num : nums) ans ^= num;
        return ans;
    }
}
```

### Java Approach 2

```java
class Solution {
	public int singleNumber(int[] nums) {
		HashSet<Integer> set = new HashSet<Integer>();
		for(int i : nums) {
			if(set.contains(i)) set.remove(i);
			else set.add(i);
		}
		return set.iterator().next();
	}
}
```

### Java Approach 3

```java
class Solution {
	public int singleNumber(int[] nums) {
		Arrays.sort(nums);
		for(int i = 1; i < nums.length; i+=2) {
			if(nums[i] != nums[i-1]) {
				return nums[i-1];
			}
		}
		return nums[nums.length-1];
	}
}
```
