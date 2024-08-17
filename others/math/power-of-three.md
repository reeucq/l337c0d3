# Question

Given an integer `n`, return _`true` if it is a power of three. Otherwise, return `false`._

## Leetcode Link

[326. Power of Three](https://leetcode.com/problems/power-of-three/)

## Approaches

1. **Iterative Approach**: Keep dividing the number by 3 until it becomes 1. If the number becomes 1, then it is a power of 3. Otherwise, it is not a power of 3.

2. **Logarithmic Approach**: If `n` is a power of 3, then `log3(n)` will be an integer. We can check if `log3(n)` is an integer or not.

3. **Direct Approach**: We can directly check if `n` is divisible by the maximum power of 3 that can be stored in an integer.

## Solutions

### Iterative Approach

```java
bool isPowerOfThree(int n) {
	if(!n) return false;
	while(n % 3 == 0) n /= 3;
	return n == 1;
}
```

### Logarithmic Approach

```java
class Solution {
    public boolean isPowerOfThree(int n) {
        if(n <= 0) return false;
        double logB3 = Math.log(n) / Math.log(3);
        return Math.pow(3, Math.round(logB3)) == n;
    }
}
```

### Direct Approach

```java
public class Solution {
    public boolean isPowerOfThree(int n) {
        // 1162261467 is 3^19,  3^20 is bigger than int
        return ( n>0 &&  1162261467%n==0);
    }
}
```
