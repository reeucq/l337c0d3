# Question

There are `n` friends that are playing a game. The friends are sitting in a circle and are numbered from `1` to `n` in **clockwise order**. More formally, moving clockwise from the `ith` friend brings you to the `(i+1)th` friend for `1 <= i < n`, and moving clockwise from the `nth` friend brings you to the `1st` friend.

The rules of the game are as follows:

1. **Start** at the `1st` friend.
2. Count the next `k` friends in the clockwise direction **including** the friend you started at. The counting wraps around the circle and may count some friends more than once.
3. The last friend you counted leaves the circle and loses the game.
4. If there is still more than one friend in the circle, go back to step 2 **starting** from the friend **immediately clockwise** of the friend who just lost and repeat.
5. Else, the last friend in the circle wins the game.

Given the number of friends, `n`, and an integer `k`, return the _winner of the game_.

## Leetcode Link

[1823. Find the Winner of the Circular Game](https://leetcode.com/problems/find-the-winner-of-the-circular-game/)

## Approaches

1. **Simulation**: We can simulate the game by using a list to represent the friends. We can keep track of the current index and remove the friend at that index. We can then update the index and repeat the process until there is only one friend left. This approach has a time complexity of $O(n^2)$ and a space complexity of $O(n)$.

2. **Iterative Josephus Problem**: We can solve this problem using the iterative Josephus problem. The Josephus problem is a theoretical problem related to a certain counting-out game. In this problem, we have `n` people standing in a circle, and we eliminate every `kth` person until only one person remains. The iterative Josephus problem is a generalization of the Josephus problem where the counting starts from a given position instead of always starting from the first person. We can use the iterative Josephus problem to find the winner of the circular game. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$. The key to understanding this solution is to see how it builds up from smaller circles to larger ones, using the result from the previous step to calculate the next one.

## Solutions

### Java Approach 1

```java
class Solution {
    public int findTheWinner(int n, int k) {
        ArrayList<Integer> al = new ArrayList<>();
        for (int i = 1; i <= n; i++) al.add(i);

        int cpIdx = 0;

        while (al.size() > 1) {
            cpIdx = (cpIdx + k - 1) % al.size();
            al.remove(cpIdx);
        }

        return al.get(0);
    }
}
```

### Java Approach 2

```java
public int findTheWinner(int n, int k) {
    int result = 1;
    for (int i = 2; i <= n; i++) {
        result = (result + k - 1) % i + 1;
    }
    return result;
}
```
