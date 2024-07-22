# Question

You are given an integer array `nums`. Let `product` be the product of all values in the array `nums`. Return _the **sign** of the **product**_.

## Leetcode Link

[1822. Sign of the Product of an Array](https://leetcode.com/problems/sign-of-the-product-of-an-array/)

## Approaches

1. **Brute Force**: We don't need to actually multiply all numbers, we can just keep track of the number of negative numbers and determine whether our product will be negative or positive. This approach has a time complexity of O(n) and a space complexity of O(1).

## Solutions

### Java Approach 1

```java
class Solution {
    public int arraySign(int[] nums) {
        int sign = 1;
        for (int i : nums) {
            if (i == 0) return 0;
            if (i < 0) sign *= -1;
        }
        return sign;
    }
}
```

### Java Approach 1

```java
class Solution {
    public int arraySign(int[] nums) {
        int positive = 0;
        int negative = 0;
        for(int num : nums) {
            if(num > 0) positive++;
            else if(num < 0) negative++;
            else return 0;
        }
        if(negative % 2 == 1) return -1;
        return 1;
    }
}
```
