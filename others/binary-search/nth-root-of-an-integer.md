# Question

You are given 2 numbers `(n , m)`; the task is to find `n√m` (nth root of m).

## GFG Link

[Find the Nth root of M](https://www.geeksforgeeks.org/problems/find-nth-root-of-m5843/)

## Approaches

1. **Binary Search**: We can use binary search to find the nth root of a number. The time complexity of this approach is $O(n * \log m)$.

## Solutions

### Java Approach 1

```java
class Solution
{
    public int NthRoot(int n, int m)
    {
        // code here
        int l = 1;
        int r = m;

        while(l <= r) {
            int mid = l + (r-l)/2;

            if(Math.pow(mid,n) == m) {
                return mid;
            }
            else if(Math.pow(mid,n) <= m) {
                l = mid + 1;
            } else {
                r = mid - 1;
            }
        }

        return -1;
    }
}
```
