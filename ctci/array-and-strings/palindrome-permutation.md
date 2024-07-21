# Question

Given a string, write a function to check if it is a permutation of a palindrome. A palindrome is a word or phrase that is the same forwards and backwards. A permutation is a rearrangement of letters. The palindrome does not need to be limited to just dictionary words.

## Approaches

1. **Brute Force**: Generate all permutations of the string and check if any of them is a palindrome. This approach is not feasible as the number of permutations of a string of length `n` is `n!`.

2. **Count Characters**: A palindrome is a string that reads the same forwards and backwards. If a string is a permutation of a palindrome, it means that the string can be rearranged to form a palindrome. A palindrome has the following properties:

   - If the length of the string is even, each character in the string must appear an even number of times.
   - If the length of the string is odd, each character in the string must appear an even number of times except for one character which can appear an odd number of times.
     We can use a hash table to count the number of times each character appears in the string. If the string is a permutation of a palindrome, the hash table will contain at most one character with an odd count.

   **Complexity Analysis**:

   - Time complexity: `O(n)` where `n` is the length of the string.
   - Space complexity: `O(c)` where `c` is the number of unique characters in the string.

## Solutions

### Java Approach 2

```java
public static boolean palindromePermutation(String s) {
    s = s.toLowerCase();
    int[] cc = new int[26];
    for (char c : s.toCharArray())
        if ('a' <= c && c <= 'z')
            cc[c - 'a']++;
    int oddCount = 0;
    for (int count : cc) {
        if (count % 2 == 1)
            oddCount++;
        if (oddCount > 1)
            return false;
    }
    return true;
}
```

**Note**: If the string contains characters other than lowercase alphabets, we can modify our code to use a hash table instead of an array to count the characters but the approach remains the same.
