# Question

There are `n` people standing in a line labeled from `1` to `n`. The first person in the line is holding a pillow initially. Every second, the person holding the pillow passes it to the next person standing in the line. Once the pillow reaches the end of the line, the direction changes, and people continue passing the pillow in the opposite direction.

For example, once the pillow reaches the `nth` person they pass it to the `n - 1th` person, then to the `n - 2th` person and so on.

Given the two positive integers n and time, return the index of the person holding the pillow after time seconds.

## Leetcode Link

[2582. Pass the Pillow](https://leetcode.com/problems/pass-the-pillow/)

## Approaches

1. **Simulation**: We can simulate the passing of the pillow by keeping track of the current position and the direction of movement. We can update the position and direction based on the current time. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

2. **Mathematical**: We can use the formula `time % n` to calculate the index of the person holding the pillow after `time` seconds. This approach has a time complexity of $O(1)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```Java
class Solution {
    public int passThePillow(int n, int time) {
        int d = 0; // 0 denotes forward direction, 1 denotes backward direction
        int c = 1;
        while(time != 0) {
            System.out.print(c+" -> ");

            if(d == 0) c++;
            if(d == 1) c--;

            if(c == 1) d = 0;
            if(c == n) d = 1;

            time--;
        }
        System.out.print(c);
        return c;
    }
}
```

### Java Approach 2

```Java
class Solution {
    public int passThePillow(int n, int time) {
        int hops = n-1; // for 1 -> 2 -> 3 -> 4 (there are 3 hops - denoted by no. of arrows)
        int rounds = time/hops; // no. of absolute rounds
        // if the no. of rounds is even, the remaining hops are from left direction
        // otw its from right direction
        return (rounds % 2 == 0) ? 1 + time % hops : n - time % hops;
    }
}
```
