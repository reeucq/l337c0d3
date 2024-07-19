# Question

Given an array `nums` of `n` integers where `nums[i]` is in the range `[1, n]`, return _an array of all the integers in the range `[1, n]` that do not appear in `nums`._

## Leetcode Link

[448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)

## Approaches

1. **Using Negative Indexing**:

   - We can use the array itself to mark the presence of a number.
   - We can iterate over the array and mark the presence of a number by making the number at the index `nums[i] - 1` negative.
   - In the second iteration, we can find the missing numbers by checking the positive numbers in the array.
   - **Complexity Analysis**:
     - Time Complexity: $O(n)$
     - Space Complexity: $O(1)$

2. **Using Cyclic Sort**:

   - We can use cyclic sort to place the numbers at their correct index.
   - In the second iteration, we can find the missing numbers by checking the numbers that are not at their correct index.
   - **Complexity Analysis**:
     - Time Complexity: $O(n)$
     - Space Complexity: $O(1)$

3. **Using Extra Space**:
   - We can use a hash set to store the numbers that are present in the array.
   - In the second iteration, we can find the missing numbers by checking the numbers that are not present in the hash set.
   - **Complexity Analysis**:
     - Time Complexity: $O(n)$
     - Space Complexity: $O(n)$

## Solutions

### Java Approach 1

```java
class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        for(int num : nums) {
            int index = Math.abs(num);
            if(nums[index - 1] > 0) {
                nums[index - 1] *= -1;
            }
        }
        List<Integer> res = new ArrayList<>();
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] > 0) res.add(i+1);
        }
        return res;
    }
}
```

### Java Approach 2

```java
import java.util.ArrayList;
import java.util.List;

public class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int i = 0;
        while (i < nums.length) {
            int correctPos = nums[i] - 1;
            if (nums[i] != nums[correctPos]) {
                // Swap
                int temp = nums[i];
                nums[i] = nums[correctPos];
                nums[correctPos] = temp;
            } else {
                i++;
            }
        }

        List<Integer> result = new ArrayList<>();
        for (i = 0; i < nums.length; i++) {
            if (nums[i] != i + 1) {
                result.add(i + 1);
            }
        }

        return result;
    }
}
```

### Java Approach 3

```java
public class Solution {
    public List<Integer> findDisappearedNumbers(int[] nums) {
        int n = nums.length;
        Set<Integer> numSet = new HashSet<>();

        // Add all numbers from the array to the set
        for (int num : nums) {
            numSet.add(num);
        }

        List<Integer> result = new ArrayList<>();

        // Check which numbers from 1 to n are missing in the set
        for (int i = 1; i <= n; i++) {
            if (!numSet.contains(i)) {
                result.add(i);
            }
        }

        return result;
    }
}
```
