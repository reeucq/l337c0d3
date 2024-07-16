# Question

The **next greater element** of some element `x` in an array is the **first greater** element that is **to the right** of `x` in the same array.

You are given two **distinct 0-indexed** integer arrays `nums1` and `nums2`, where `nums1` is a subset of `nums2`.

For each `0 <= i < nums1.length`, find the index `j` such that `nums1[i] == nums2[j]` and determine the **next greater element** of `nums2[j]` in `nums2`. If there is no next greater element, then the answer for this query is `-1`.

Return _an array `ans` of length `nums1.length `such that `ans[i]` is the **next greater element** as described above._

## Leetcode Link

[496. Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)

## Approaches

1. **Using Stack & HashMap**: We use a stack to keep track of elements from `nums2` that we haven't found a next greater element for yet. We iterate through `nums2` once and for each element: While the stack is not empty and the current element is greater than the top of the stack, we've found the next greater element for the top of the stack. We pop it and add this information to the hash map and push the current element to the stack. Since we have now gotten the list of next greater elements for all the elements. We can just fill them up in result array for numbers given to us. This has a time complexity of $O(n)$ where `n` is the length of `nums2` and space complexity of $O(n)$ as well.

2. **Using Only HashMap**: We can use a hashmap to store the indices of all the numbers in `nums` and then for each number in `nums1` we can find the index of the number in `nums2` and then iterate through `nums2` from that index to find the next greater element. This has a time complexity of $O(n*m)$ and space complexity of $O(n)$ as well.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        Map<Integer, Integer> nextGreater = new HashMap<>();
        Stack<Integer> stack = new Stack<>();

        // Build the nextGreater map for nums2
        for (int num : nums2) {
            while (!stack.isEmpty() && stack.peek() < num) {
                nextGreater.put(stack.pop(), num);
            }
            stack.push(num);
        }

        // Build the result array for nums1
        int[] result = new int[nums1.length];
        for (int i = 0; i < nums1.length; i++) {
            result[i] = nextGreater.getOrDefault(nums1[i], -1);
        }

        return result;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int[] nextGreaterElement(int[] nums1, int[] nums2) {
        HashMap<Integer,Integer> hm = new HashMap<>();
        for(int i = 0; i < nums2.length; i++) hm.put(nums2[i],i);
        int[] res = new int[nums1.length];
        int k = 0;

        for(int num : nums1) {
            res[k++] = findNextGreater(nums2, hm.get(num));
        }

        return res;
    }

    private int findNextGreater(int[] nums, int start) {
        if(start == nums.length - 1) return -1;
        for(int i = start+1; i < nums.length; i++) {
            if(nums[i] > nums[start]) return nums[i];
        }
        return -1;
    }
}
```
