# Question

Given a positive integer `num`, return _`true` if `num` is a perfect square or `false` otherwise._

## Leetcode Link

[367. Valid Perfect Square](https://leetcode.com/problems/valid-perfect-square/)

## Approach

1. **Binary Search**: We can use binary search to find the square root of the number. We can start with the range 0 to `num/2` and keep dividing the range in half until we find the square root without taking into account the decimal part. If the square of the number is equal to the number, we return `true`, otherwise `false`. The time complexity is $O(\log n)$.

2. **Mathematics - Sum of Odd Numbers**: We can use the property of perfect squares. The property states that every perfect square is the sum of consecutive odd numbers starting from 1. We can start with 1 and keep subtracting the odd numbers from the number until the number becomes 0. If the number becomes 0, we return `true`, otherwise `false`. The time complexity is $O(\sqrt n)$. We alr know:

   ```
   1 = 1
   4 = 1 + 3
   9 = 1 + 3 + 5
   16 = 1 + 3 + 5 + 7
   25 = 1 + 3 + 5 + 7 + 9
   36 = 1 + 3 + 5 + 7 + 9 + 11
   .
   .
   .
   1+3+...+(2n-1) = (2n-1 + 1)n/2 = nn
   ```

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        if(num < 2) return true;

        long l = 2;
        long r = num / 2;

        while(l <= r) {
            long m = l + (r-l)/2;
            long sq = m * m;

            if(sq == num) return true;
            else if(sq < num) l = m + 1;
            else r = m - 1;
        }

        return false;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean isPerfectSquare(int num) {
        int i = 1;
        while (num > 0) {
            num -= i;
            i += 2;
        }
        return num == 0;
    }
}
```
