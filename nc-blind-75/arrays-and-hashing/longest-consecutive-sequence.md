# Question

Given an unsorted array of integers `nums`, return the _length of the longest consecutive elements sequence_.
You must write an algorithm that runs in `O(n)` time.

## Leetcode Link

[128. Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence/)

## Approaches

1. **Brute Force**: Run a loop for each element and check for the consecutive elements. Time complexity: $O(n^2)$

2. **Sorting**: Sort the array and then find the longest consecutive sequence. Time complexity: $O(n \log n)$

3. **Hashing**: Store all the elements in a set and then check for the consecutive elements. Time complexity: $O(n)$

## Solutions

### Java Approach 1

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if(nums.length == 0) return 0;
        int longestStreak = 1;

        for(int num : nums) {
            int currentNum = num;
            int currentStreak = 1;

            while(arrayContains(nums,currentNum+1)) {
                currentNum += 1;
                currentStreak += 1;
            }

            longestStreak = Math.max(longestStreak, currentStreak);
        }

        return longestStreak;
    }

    private boolean arrayContains(int[] nums, int num) {
        for(int i : nums) {
            if(i == num) return true;
        }

        return false;
    }
}
```

### Java Approach 2

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if(nums.length == 0) return 0;

        Arrays.sort(nums);
        int longest = 1;
        int currentStreak = 0;
        int lastSmallest = Integer.MIN_VALUE;

        for(int num : nums) {
            if(lastSmallest == num-1) {
                currentStreak++;
            } else if(lastSmallest != num) {
                currentStreak = 1;
            }

            lastSmallest = num;
            longest = Math.max(longest, currentStreak);
        }

        return longest;
    }
}
```

### Java Approach 3

```java
class Solution {
    public int longestConsecutive(int[] nums) {
        if (nums == null || nums.length == 0) return 0;

        // Step 1: Add all numbers to a HashSet
        Set<Integer> numSet = new HashSet<>();
        for (int num : nums) {
            numSet.add(num);
        }

        int longestStreak = 0;

        // Step 2: Iterate through the array
        for (int num : nums) {
            // Step 3: Check if it's the start of a sequence
            if (!numSet.contains(num - 1)) {
                int currentNum = num;
                int currentStreak = 1;

                // Step 4: Count the length of the sequence
                while (numSet.contains(currentNum + 1)) {
                    currentNum++;
                    currentStreak++;
                }

                // Step 5: Update the longest streak
                longestStreak = Math.max(longestStreak, currentStreak);
            }
        }

        return longestStreak;
    }
}
```
