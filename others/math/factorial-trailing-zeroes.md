# Question

Given an integer `n`, return _the number of trailing zeroes in n!_.

Note that `n! = n * (n - 1) * (n - 2) * ... * 3 * 2 * 1.`

## Leetcode Link

[172. Factorial Trailing Zeroes](https://leetcode.com/problems/factorial-trailing-zeroes/)

## Approaches

1. **Brute Force**: We can calculate the factorial of `n` and count the number of trailing zeroes. This approach has a time complexity of `O(n^2 log n)` due to the calculation of the factorial and a space complexity of `O(n)` where n is the number of digits in the factorial.

2. **Counting 5s**: We can count the number of 5s in the factorial of `n`. This is because the number of 5s will determine the number of trailing zeroes in the factorial. We can count the number of 5s by dividing `n` by 5, then dividing the result by 5, and so on. This approach has a time complexity of `O(log n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public int trailingZeroes(int n) {
        double sum = 0;
        for(int i = 2; i <= n; i++) {
            sum += Math.log10(i);
        }
        int m = (int) Math.floor(sum) + 1;
        int[] f = new int[m];
        int j = m - 1;
        f[m - 1] = 1;

        for(int i = 2; i <= n; i++) {
            int c = 0;
            for(int k = m - 1; k >= j; k--) {
                int x = i * f[k] + c;
                f[k] = x % 10;
                c = x / 10;
            }

            while(c != 0) {
                j--;
                f[j] = c % 10;
                c = c / 10;
            }
        }

        int noOfZeroes = 0;
        for(int i = m - 1; i >= 0; i--) {
            if(f[i] != 0) break;
            else noOfZeroes++;
        }

        return noOfZeroes;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int trailingZeroes(int n) {
        int noOfZeroes = 0;
        while(n != 0) {
            int tmp = n / 5;
            noOfZeroes += tmp;
            n = tmp;
        }
        return noOfZeroes;
    }
}
```
