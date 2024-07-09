# Question

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, _return the only number in the range that is missing from the array_.

## Leetcode Link

[286. Missing Number](https://leetcode.com/problems/missing-number/)

## Approaches

1. **Hashing**: We can create a hash array and mark the numbers present in the input array. Then, we can iterate over the hash array to find the missing number. This approach has a time complexity of $O(n)$ and a space complexity of $O(n)$.

2. **Using Natural Sum**: We can calculate the sum of the first `n` natural numbers using the formula `n * (n + 1) / 2`. Then, we can calculate the sum of the input array. The difference between the two sums will be the missing number. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

3. **Using XOR**: We can use the XOR operation to find the missing number. We can XOR all the numbers in the input array and then XOR all the numbers in the range `[0, n]`. The result will be the missing number. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int missingNumber(int[] nums) {
        int n = nums.length;
        int[] v = new int[n+1];
        Arrays.fill(v, -1);
        for(int i = 0; i < nums.length; i++) {
            v[nums[i]] = nums[i];
        }
        for(int i = 0; i < v.length; i++) {
            if(v[i] == -1) return i;
        }
        return 0;
    }
}

```

### Java Approach 2

```java
class Solution {
    public int missingNumber(int[] nums) {
        int requiredSum = 0, actualSum = 0;
        for(int i = 0; i < nums.length; i++) {
            requiredSum += i;
            actualSum += nums[i];
        }
        return (requiredSum + nums.length) - actualSum;
    }
}
```

### Java Approach 3

```java
public int missingNumber(int[] nums) {
    int xor = 0, i = 0;
	for (i = 0; i < nums.length; i++) {
		xor = xor ^ i ^ nums[i];
	}
	return xor ^ i;
}
```
