# Question

Given two strings, write a method to decide if one is a permutation of the other.

## Approaches

1. **Sorting**: We can sort both strings and compare them. If the sorted strings are equal, the strings are permutations of each other. This approach has a time complexity of $O(n \log n)$ and a space complexity of $O(n)$.

2. **Frequency Count**: We can count the frequency of characters in both strings and compare the counts. If the counts are equal, the strings are permutations of each other. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java Approach 1

```java
public static boolean checkPermutationSorting(String a, String b) {
        return sort(a).equals(sort(b));
    }

    public static String sort(String s) {
        char[] letters = s.toCharArray();
        Arrays.sort(letters);
        return new String(letters);
    }
```

### Java Approach 2

```java
public static boolean checkPermutationFrequency(String a, String b) {
    if (a.length() != b.length()) return false;

    int[] count = new int[128]; // Assuming ASCII
    for (char c : a.toCharArray())
        count[c]++;

    for (char c : b.toCharArray()) {
        count[c]--;
        if (count[c] < 0)
            return false;
    }

    return true;
}
```
