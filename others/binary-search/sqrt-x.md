# Question

Given a non-negative integer `x`, return _the square root of x rounded down to the nearest integer_. The returned integer should be **non-negative** as well.

## Leetcode Link

[69. Sqrt(x)](https://leetcode.com/problems/sqrtx/)

## Approaches

1. **Binary Search**: We can use binary search to find the square root of a number. The time complexity of this approach is $O(\log x)$.

2. **Babylonian Method**: This method is also known as Heron's method. It is an iterative method to find the square root of a number. The time complexity of this approach is $O(\log x)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int mySqrt(int x) {
        int l = 1;
        int r = x;
        int ans = 0;

        while(l <= r) {
            int m = l + (r-l)/2;

            if(m <= x / m) { // to prevent overflow
                l = m+1;
                ans = m;
            } else {
                r = m-1;
            }
        }

        return ans;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int mySqrt(int x) {
        double guess1 = x;
        double guess2 = 1.0;

        while(Math.abs(guess1-guess2) > 0.00001) {
            guess1 = guess2;
            guess2 = (guess1 + (x/guess1))/2;
        }

        return (int)guess2;
    }
}
```
