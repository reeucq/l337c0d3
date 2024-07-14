# Question

You are given an array of strings `words` and a string `chars`.

A string is **good** if it can be formed by characters from `chars` (each character can only be used once).

Return _the sum of lengths of all good strings in words._

## Leetcode Link

[1160. Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)

## Approaches

1. **Count Characters in `chars`**: We can count the frequency of each character in `chars` and store it in a array. For each word in `words`, we can count the frequency of each character in the word and compare it with the frequency of characters in `chars`. If the word can be formed by characters from `chars`, we add the length of the word to the result. This approach has a time complexity of $O(n \cdot m)$ and a space complexity of $O(1)$, where `n` is the number of words and `m` is the length of the longest word.

## Solutions

### Java Approach 1

```java
class Solution {
    public int countCharacters(String[] words, String chars) {
        int[] charCount = new int[26];
        for (char c : chars.toCharArray()) charCount[c - 'a']++;

        int sum = 0;
        for (String word : words) {
            if (isGood(charCount, word)) {
                sum += word.length();
            }
        }

        return sum;
    }

    public boolean isGood(int[] charCount, String word) {
        int[] tempCount = new int[26];
        for (char c : word.toCharArray()) {
            int index = c - 'a';
            tempCount[index]++;
            if (tempCount[index] > charCount[index]) {
                return false;
            }
        }
        return true;
    }
}
```
