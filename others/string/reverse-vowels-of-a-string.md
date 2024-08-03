# Question

Given a string `s`, reverse only all the vowels in the string and return _it_.

## Leetcode Link

[345. Reverse Vowels of a String](https://leetcode.com/problems/reverse-vowels-of-a-string/)

## Approaches

1. **Two-Pointer Approach**: We can use a two-pointer approach to swap the vowels in the string. We can start with two pointers, one at the beginning of the string and the other at the end. We can then move the pointers towards each other, swapping the vowels at each position. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public String reverseVowels(String s) {
        int l = 0;
        int r = s.length() - 1;
        char[] letters = s.toCharArray();

        while(l < r) {
            if(isVowel(letters[l]) && isVowel(letters[r])) {
                char temp = letters[l];
                letters[l] = letters[r];
                letters[r] = temp;
                l++;
                r--;
            }

            if(!isVowel(letters[l])) l++;
            if(!isVowel(letters[r])) r--;
        }
        return new String(letters);
    }

    private boolean isVowel(char c) {
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u' || c == 'A' || c == 'E' || c == 'I' || c == 'O' || c == 'U';
    }
}
```
