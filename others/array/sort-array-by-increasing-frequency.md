# Question

Given an array of integers `nums`, sort the array in **increasing** order based on the frequency of the values. If multiple values have the same frequency, sort them in **decreasing** order.

Return _the sorted array_.

## Leetcode Link

[1636. Sort Array by Increasing Frequency](https://leetcode.com/problems/sort-array-by-increasing-frequency/)

## Approaches

1. **Using HashMap & Comparator**: We'll first collect all the frequencies of the elements in the array in a hashmap and use a custom comparator to sort the elements based on the frequency and the value itself. This approach has a time complexity of $O(nlogn)$ and a space complexity of $O(n)$.

2. **Counting Sort**: This'll work if the no. of elements in the array are fixed and the array value is also fixed (which is the case in this question statement on lc). This has a time complexity of $O(n^2)$ and a space complexity of $O(1)$ since we'll use a fixed size array to store count and it is more efficient than the previous approach. It also works in place.

## Solutions

### Java Approach 1

```java
class Solution {
    public int[] frequencySort(int[] nums) {
        HashMap<Integer,Integer> hm = new HashMap<>();
        for(int num : nums) hm.put(num, hm.getOrDefault(num,0)+1);
        List<Integer> list = new ArrayList<>(hm.keySet());
        Collections.sort(list,(a,b) -> {
            int freqCompare = hm.get(a).compareTo(hm.get(b));
            if(freqCompare != 0) return freqCompare;
            return b.compareTo(a);
        });
        int[] res = new int[nums.length];
        int k = 0;
        for(int i = 0; i < list.size(); i++) {
            int count = hm.get(list.get(i));
            while(count > 0) {
                res[k++] = list.get(i);
                count--;
            }
        }
        return res;
    }
}
```

### Java Approach 1 - Functional

```java
public int[] frequencySort(int[] nums) {
	Map<Integer, Integer> map = new HashMap<>();
	// count frequency of each number
	Arrays.stream(nums).forEach(n -> map.put(n, map.getOrDefault(n, 0) + 1));
	// custom sort
	return Arrays.stream(nums).boxed()
			.sorted((a,b) -> map.get(a) != map.get(b) ? map.get(a) - map.get(b) : b - a)
			.mapToInt(n -> n)
			.toArray();
}
```

### Java Approach 2

```java
class Solution {
    public int[] frequencySort(int[] nums) {
        // Step 1: Count the frequency of each number
        // We use an array of size 201 to account for the range -100 to 100
        int[] count = new int[201];
        for (int num : nums) {
            count[num + 100]++; // Shift by +100 to handle negative numbers
        }

        // Step 2: Sort the array based on frequencies
        for (int i = nums.length - 1; i >= 0;) {
            // Find the number with the highest remaining frequency
            int maxFreq = 0;
            int maxFreqIndex = -1;
            for (int j = 0; j < count.length; j++) {
                if (count[j] > maxFreq) {
                    maxFreq = count[j];
                    maxFreqIndex = j;
                }
            }

            // Place the number with highest frequency in the array
            int currentNum = maxFreqIndex - 100; // Convert back to original number
            for (int j = 0; j < maxFreq; j++) {
                nums[i] = currentNum;
                i--;
            }

            // Reset the count for the number we just placed
            count[maxFreqIndex] = 0;
        }

        return nums;
    }
}
```
