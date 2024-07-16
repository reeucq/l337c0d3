# Question

Given a circular integer array `nums` (i.e., the next element of `nums[nums.length - 1] is nums[0]`), return _the **next greater number** for every element in `nums`._

The **next greater number** of a number `x` is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, return `-1` for this number.

## Leetcode Link

[503. Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)

## Approaches

1. **Brute Force**: We can traverse circularly for each element in nums and check its next greater element. This approach will take $O(n^2)$ time complexity. The space complexity will be $O(n)$.

2. **Using Stack**: We can use a stack to store the index of elements in nums. We will traverse the nums array twice and for each element, we will check if the current element is greater than the element at the top of the stack. If it is, we will update the result array with the current element. This approach will take $O(n)$ time complexity. The space complexity will be $O(n)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int[] res = new int[nums.length];

        for(int i = 0; i < nums.length; i++) {
            res[i] = findNG(nums,i);
        }

        return res;
    }

    private int findNG(int[] nums, int start) {
        for(int i = start+1; i < nums.length + start; i++) {
            if(nums[i % nums.length] > nums[start]) return nums[i % nums.length];
        }
        return -1;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int[] nextGreaterElements(int[] nums) {
        int n = nums.length;
        int[] res = new int[n];
        Arrays.fill(res,-1);
        Stack<Integer> s = new Stack<>();

        for(int i = 0; i < n*2; i++) {
            while(!s.isEmpty() && nums[s.peek()] < nums[i%n]) {
                res[s.pop()] = nums[i%n];
            }
            if(i < n) s.push(i);
        }

        return res;
    }
}
```
