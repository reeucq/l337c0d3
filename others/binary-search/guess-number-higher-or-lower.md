# Question

We are playing the Guess Game. The game is as follows:

I pick a number from `1` to `n`. You have to guess which number I picked.

Every time you guess wrong, I will tell you whether the number I picked is higher or lower than your guess.

You call a pre-defined API `int guess(int num)`, which returns three possible results:

- `-1`: Your guess is higher than the number I picked (i.e. `num > pick`).
- `1`: Your guess is lower than the number I picked (i.e. `num < pick`).
- `0`: your guess is equal to the number I picked (i.e. `num == pick`).

Return _the number that I picked._

## Leetcode Link

[374. Guess Number Higher or Lower](https://leetcode.com/problems/guess-number-higher-or-lower/)

## Approaches

1. **Binary Search**: Since the number is between `1` to `n`, we can always make use of binary search and divide the search space in half based on the response of the Guess API. This has a time complexity of $O(log n)$.

## Solutions

### Java Approach 1

```java
public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int l = 1;
        int r = n;

        while(l <= r) {
            int m = l+(r-l)/2;

            if(guess(m) == 0) {
                return m;
            } else if(guess(m) == 1) {
                l = m+1;
            } else {
                r = m-1;
            }
        }

        return -1;
    }
}
```
