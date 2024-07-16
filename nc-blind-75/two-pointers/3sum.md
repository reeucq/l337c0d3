# Question

Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j, i != k, and j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.

## Leetcode Link

[15. 3Sum](https://leetcode.com/problems/3sum/)

## Approaches

1. **Brute Force**: We can use three nested loops to find all the triplets. This approach will take $O(n^3)$ time.

2. **HashSet**: Instead of using three loops, we can use three loops and use a hashset and store the elements between the current loop positions, if any of them form a triplet, we added it to a hashset after sorting so it doesn't contain duplicates. This approach will take $O(n^2)$ time.

3. **Two Pointers**: Instead of using HashSet and sorting before adding, we can sort the array before hand and use two pointer approach to find a triplet. We can always just move the pointers in case of a sum greater than 0 or less than 0 or when there are duplicates. This approach will take $O(n^2)$ time.

## Solutions

### Java Approach 1

```java
public static List<List<Integer>> triplet(int n, int[] arr) {
    Set<List<Integer>> st = new HashSet<>();

    // check all possible triplets:
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            for (int k = j + 1; k < n; k++) {
                if (arr[i] + arr[j] + arr[k] == 0) {
                    List<Integer> temp = Arrays.asList(arr[i], arr[j], arr[k]);
                    temp.sort(null);
                    st.add(temp);
                }
            }
        }
    }

    // store the set elements in the answer:
    List<List<Integer>> ans = new ArrayList<>(st);
    return ans;
}
```

### Java Approach 2

```java
class Solution {
    public List<List<Integer>> threeSum(int[] arr) {
         Set<List<Integer>> st = new HashSet<>();
         int n = arr.length;

        for (int i = 0; i < n; i++) {
            Set<Integer> hashset = new HashSet<>();
            for (int j = i + 1; j < n; j++) {
                //Calculate the 3rd element:
                int third = -(arr[i] + arr[j]);

                //Find the element in the set:
                if (hashset.contains(third)) {
                    List<Integer> temp = Arrays.asList(arr[i], arr[j], third);
                    temp.sort(null);
                    st.add(temp);
                }
                hashset.add(arr[j]);
            }
        }

        // store the set elements in the answer:
        List<List<Integer>> ans = new ArrayList<>(st);
        return ans;
    }
}
```

### Java Approach 3

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        Set<List<Integer>> res = new HashSet<>();
        Arrays.sort(nums);

        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue; // Skip duplicates

            int left = i + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    res.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    while (left < right && nums[left] == nums[left+1]) left++; // Skip duplicates
                    while (left < right && nums[right] == nums[right-1]) right--; // Skip duplicates
                    left++;
                    right--;
                } else if (sum < 0) {
                    left++;
                } else {
                    right--;
                }
            }
        }

        return new ArrayList<>(res);
    }
}
```
