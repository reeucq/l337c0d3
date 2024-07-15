# Question

Given a **1-indexed** array of integers `numbers` that is already **sorted in non-decreasing order**, find two numbers such that they add up to a specific `target` number. Let these two numbers be `numbers[index1]` and `numbers[index2]` where `1 <= index1 < index2 <= numbers.length`.

Return _the indices of the two numbers, `index1` and `index2`, **added by one** as an integer array `[index1, index2]` of length 2._

## Leetcode Link

[167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/)

## Approaches

1. **Two Pointers**: Since the array is sorted, we can use greedy approach, we'll initialize two pointers `i` and `j` to `0` and `numbers.length - 1` respectively. If the sum of the numbers at these indices is less than the target, we'll increment `i`, else we'll decrement `j`. We'll continue this process until we find the target sum and return the indices. This approach has a time complexity of $O(n)$ and space complexity of $O(1)$.

2. **Hash Map**: We can use a hash map to store the numbers and their indices. We'll iterate through the array and check if the difference between the target and the current number is present in the hash map. If it is, we'll return the indices of the current number and the difference. This approach has a time complexity of $O(n)$ and space complexity of $O(n)$.

3. **Binary Search**: We can use binary search to find the difference between the target and the current number. This approach has a time complexity of $O(n \log n)$ and space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int i = 0;
        int j = numbers.length -1;

        while(i < j) {
            int sum = numbers[i] + numbers[j];
            if(sum > target) j--;
            else if(sum < target) i++;
            else return new int[]{i+1,j+1};
        }

        return new int[]{};
    }
}
```

### Java Approach 2

```java
public static int[] twoSum_hash(int[] numbers, int target) {
    int len = numbers.length;
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < len; i++) {
        if (map.containsKey(target - numbers[i])) {
            return new int[]{map.get(target - numbers[i]), i + 1};
        }

        map.putIfAbsent(numbers[i], i + 1);
    }

    return new int[0];
}
```

### Java Approach 3

```java
public int[] twoSum_bs(int[] numbers, int target) {
    for (int i = 0; i < numbers.length; ++i) {
        int low = i + 1;
        int high = numbers.length - 1;
        while (low <= high) {
            int mid = (high - low) / 2 + low;
            if (numbers[mid] == target - numbers[i]) {
                return new int[]{i + 1, mid + 1};
            } else if (numbers[mid] > target - numbers[i]) {
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
    }
    return new int[]{-1, -1};
}
```
