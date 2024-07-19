# Question

Given an array `nums` of `n` integers, return _an array of all the **unique** quadruplets `[nums[a], nums[b], nums[c], nums[d]]` such that:_

- `0 <= a, b, c, d < n`
- `a`, `b`, `c`, and `d` are distinct.
- `nums[a] + nums[b] + nums[c] + nums[d] == target`

You may return the answer in **any order**.

## Approaches

1. **Brute Force**: Use 4 nested loops to find all quadruplets. Time complexity is $O(n^4)$

2. **HashSet**: Use 3 nested loops and a hashset to store the elements between the current loop positions. Time complexity is $O(n^3)$

3. **Two Pointers**: Sort the array and use two pointers to find a quadruplet. Time complexity is $O(n^3)$

## Solutions

### Java Approach 1

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Set<List<Integer>> result = new HashSet<>();
        int n = nums.length;

        for (int i = 0; i < n - 3; i++) {
            for (int j = i + 1; j < n - 2; j++) {
                for (int k = j + 1; k < n - 1; k++) {
                    for (int l = k + 1; l < n; l++) {
                        long sum = (long)nums[i] + nums[j] + nums[k] + nums[l];
                        if (sum == target) {
                            List<Integer> quadruplet = Arrays.asList(nums[i], nums[j], nums[k], nums[l]);
                            Collections.sort(quadruplet);
                            result.add(quadruplet);
                        }
                    }
                }
            }
        }

        return new ArrayList<>(result);
    }
}
```

### Java Approach 2

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        Set<List<Integer>> result = new HashSet<>();
        int n = nums.length;

        for (int i = 0; i < n - 3; i++) {
            for (int j = i + 1; j < n - 2; j++) {
                Set<Long> complementSet = new HashSet<>();
                for (int k = j + 1; k < n; k++) {
                    long complement = (long)target - nums[i] - nums[j] - nums[k];
                    if (complementSet.contains(complement)) {
                        List<Integer> quadruplet = Arrays.asList(nums[i], nums[j], (int)complement, nums[k]);
                        Collections.sort(quadruplet);
                        result.add(quadruplet);
                    }
                    complementSet.add((long)nums[k]);
                }
            }
        }

        return new ArrayList<>(result);
    }
}
```

### Java Approach 3

```java
class Solution {
    public List<List<Integer>> fourSum(int[] nums, int target) {
        Arrays.sort(nums);
        Set<List<Integer>> res = new HashSet<>();
        int n = nums.length;

        for (int i = 0; i < n - 3; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue; // Skip duplicates for i

            for (int j = i + 1; j < n - 2; j++) {
                if (j > i + 1 && nums[j] == nums[j-1]) continue; // Skip duplicates for j

                int left = j + 1;
                int right = n - 1;

                while (left < right) {
                    // Use long to prevent integer overflow
                    long sum = (long)nums[i] + nums[j] + nums[left] + nums[right];

                    if (sum == target) {
                        res.add(Arrays.asList(nums[i], nums[j], nums[left], nums[right]));

                        // Skip duplicates for left and right
                        while (left < right && nums[left] == nums[left+1]) left++;
                        while (left < right && nums[right] == nums[right-1]) right--;

                        left++;
                        right--;
                    } else if (sum < target) {
                        left++;
                    } else {
                        right--;
                    }
                }
            }
        }

        return new ArrayList<>(res);
    }
}
```
