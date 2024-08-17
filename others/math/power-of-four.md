# Question

Given an integer `n`, return _`true` if it is a power of four. Otherwise, return `false`._

## Leetcode Link

[342. Power of Four](https://leetcode.com/problems/power-of-four/)

## Approaches

1. **Iterative Approach**: Keep dividing the number by 4 until it becomes 1. If the number is not divisible by 4, return `false`. If the number becomes 1, return `true`.

2. **Bit Manipulation**: A number is a power of 4 if it is a power of 2 and the only set bit is at an odd position.

3. **Logarithm Approach**: If `n` is a power of 4, then `log4(n)` will be an integer.

## Solutions

### Java Approach 1

```java
bool isPowerOfFour(int n) {
    if(n==0){
        return false;
    }
    while(n%4 == 0){
        n /= 4;
    }
    return n==1;
}
```

### Java Approach 2

```java
public class Solution {
    public boolean isPowerOfFour(int num) {
        return (num > 0) && ((num & (num - 1)) == 0) && ((num & 0x55555555) == num);
    }
}
```

### Java Approach 3

```java
class Solution {
    public boolean isPowerOfFour(int n) {
        if(n <= 0) return false;
        double logB4 = Math.log(n) / Math.log(4);
        return Math.pow(4, Math.round(logB4)) == n;
    }
}
```
