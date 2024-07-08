# Question

Given two integer arrays `nums1` and `nums2`, _return an array of their intersection_. Each element in the result must be **unique** and you may return the result in **any order**.

## Leetcode Link

[349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays)

## Approaches

1. **Using Set**: We can use set to store the elements of the first array and then iterate over the second array to check if the element is present in the set. If it is present, we add it to the result set. Finally, we convert the result set to a list and return it. This has a time complexity of $O(n)$ where n is the size of the larger array and a space complexity of $O(n)$ where n is the size of the smaller array.

2. **Sorting**: We can sort both the arrays and then iterate over them to find the common elements. We can use two pointers to iterate over the arrays. If the elements are equal, we add it to the result set. If the element in the first array is smaller, we increment the first pointer. If the element in the second array is smaller, we increment the second pointer. Finally, we convert the result set to a list and return it. It has a time complexity of $O(n\log n)$ where n is the size of the larger array and a space complexity of $O(n)$ where n is the size of the smaller array.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        if(nums1.length > nums2.length) return intersection(nums2,nums1);
        HashSet<Integer> set = new HashSet<>();
        for(int num : nums1) set.add(num);
        ArrayList<Integer> res = new ArrayList<>();
        for(int num : nums2) if(set.remove(num)) res.add(num);
        int[] result = new int[res.size()];
        for(int i = 0; i < res.size(); i++) result[i] = res.get(i);
        return result;
    }
}
```

### Java Approach 2

```java
public class Solution {
    public int[] intersection(int[] nums1, int[] nums2) {
        Set<Integer> set = new HashSet<>();
        Set<Integer> intersect = new HashSet<>();
        for (int i = 0; i < nums1.length; i++) {
            set.add(nums1[i]);
        }
        for (int i = 0; i < nums2.length; i++) {
            if (set.contains(nums2[i])) {
                intersect.add(nums2[i]);
            }
        }
        int[] result = new int[intersect.size()];
        int i = 0;
        for (Integer num : intersect) {
            result[i++] = num;
        }
        return result;
    }
}
```
