# Question

Given an array `arr` containing `n` integers and an integer `k`. Your task is to find the length of the longest Sub-Array with the sum of the elements equal to the given value `k`.

## GFG Link

[Longest sub-array with sum k](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/)

## Approaches

1. **Brute Force**: Generate all possible subarrays and check if the sum of the subarray is equal to `k`. Time complexity: $O(n^2)$, Space complexity: $O(1)$

2. **Hashing**: Use a hashmap to store the prefix sum of the array along with index where it happens. If the prefix sum is `sum` and we have already seen `sum-k` before, then the subarray between the two indices will have sum `k`. Time complexity: $O(n)$, Space complexity: $O(n)`

3. **Sliding Window**: Maintain a window of elements such that the sum of the elements in the window is equal to `k`. Time complexity: $O(n)$, Space complexity: $O(1)$ but this only works for positive numbers.

## Solutions

### Java Approach 1

```java
public static int lenOfLongSubarr(int A[], int N, int K) {
    int maxLen = 0;
    for (int i = 0; i < N; i++) {
        int sum = 0;
        for (int j = i; j < N; j++) {
            sum += A[j];
            if (sum == K) {
                maxLen = Math.max(maxLen, j - i + 1);
            }
        }
    }
    return maxLen;
}
```

### Java Approach 2

```java
public static int lenOfLongSubarr(int A[], int N, int K) {
    Map<Long, Integer> prefixSumIndex = new HashMap<>();
    long sum = 0;
    int maxLen = 0;

    // Important: Handle the case where the subarray starts from index 0
    prefixSumIndex.put(0L, -1);

    for (int i = 0; i < N; i++) {
        sum += A[i];

        if (prefixSumIndex.containsKey(sum - K)) {
            maxLen = Math.max(maxLen, i - prefixSumIndex.get(sum - K));
        }

        // Only put this sum in the map if it's not already there
        // This ensures we keep the earliest occurrence of the sum
        prefixSumIndex.putIfAbsent(sum, i);
    }

    return maxLen;
}
```

### Java Approach 3

```java
public static int lenOfLongSubarr(int A[], int N, int K) {
    int start = 0, end = 0;
    int sum = 0;
    int maxLen = 0;

    while (end < N) {
        // Expand the window
        sum += A[end];

        // Contract the window if sum becomes greater than K
        while (sum > K && start <= end) {
            sum -= A[start];
            start++;
        }

        // Update maxLen if sum equals K
        if (sum == K) {
            maxLen = Math.max(maxLen, end - start + 1);
        }

        end++;
    }

    return maxLen;
}
```
