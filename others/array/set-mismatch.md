# Question

You have a set of integers `s`, which originally contains all the numbers from `1` to `n`. Unfortunately, due to some error, one of the numbers in `s` got duplicated to another number in the set, which results in **repetition of one number** and **loss of another number**.

You are given an integer array `nums` representing the data status of this set after the error.

Find the number that occurs twice and the number that is missing and return _them in the form of an array._

## Leetcode Link

[645. Set Mismatch](https://leetcode.com/problems/set-mismatch/)

## Approaches

1. **Use Array as Set**: Since we know the range of the numbers is from `1` to `n`, then we can iterate over the array and keep track of the numbers that we have seen by marking it as negative. If we encounter a number that's already negative, then it's the duplicate number. The missing number is the one that is positive, so we'll iterate over the array again to find it. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] findErrorNums(int[] nums) {
        int duplicateNum = 0;
        for(int i = 0; i < nums.length; i++) {
            int idx = Math.abs(nums[i]);
            if(nums[idx-1] < 0) duplicateNum = Math.abs(nums[i]);
            if(nums[idx-1] > 0) nums[idx-1] *= -1;
        }

        for(int i = 0; i < nums.length; i++) {
            if(nums[i] > 0) return new int[]{duplicateNum,i+1};
        }

        return new int[]{};
    }
}
```
