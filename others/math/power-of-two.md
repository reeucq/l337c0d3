# Question

Given an integer `n`, return _`true` if it is a power of two. Otherwise, return `false`._

## Leetcode Link

[231. Power of Two](https://leetcode.com/problems/power-of-two/)

## Approaches

1. **Iterative Division**:

   - Divide the number by 2 until it becomes 1.
   - Time complexity: O(log n)
   - Space complexity: O(1)

2. **Bit Manipulation**:

   - Check if the number is a power of 2 using bitwise operations.
   - Time complexity: O(1)
   - Space complexity: O(1)

3. **Logarithm**:

   - Check if the logarithm of the number is an integer.
   - Time complexity: O(1)
   - Space complexity: O(1)

4. **Bit Count**:
   - Count the number of set bits in the binary representation of the number.
   - Time complexity: O(1)
   - Space complexity: O(1)

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n <= 0) return false;
        while (n % 2 == 0) {
            n /= 2;
        }
        return n == 1;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1)) == 0;
    }
}
```

### Java Approach 3

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if (n <= 0) return false;
        double logBase2 = Math.log(n) / Math.log(2);
        return Math.pow(2, Math.round(logBase2)) == n;
    }
}
```

### Java Approach 4

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        return n > 0 && Integer.bitCount(n) == 1;
    }
}
```
