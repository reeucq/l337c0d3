# Question

Write a method to replace all spaces in a string with `%20`. You may assume that the string has sufficient space at the end to hold the additional characters, and you are given the `true` length of the string.

Example:

```
Input: "Mr John Smith    ", 13
Output: "Mr%20John%20Smith"
```

## Approach

1. **Two Pass Algorithm**: We'll just find out the actual length of the string and then traverse from the back and keep replacing spaces with `%20` and other characters as it is. Time complexity of this approach is $O(n)$ where `n` is the length of the character array.

## Solution

```java
public static void urlify(char[] str, int trueLength) {
    int spaceCount = 0;
    for (int i = 0; i < trueLength; i++) {
        if (str[i] == ' ') {
            spaceCount++;
        }
    }

    int newLength = trueLength + spaceCount * 2;

    int index = newLength - 1;

    for (int i = trueLength - 1; i >= 0; i--) {
        if (str[i] == ' ') {
            str[index--] = '0';
            str[index--] = '2';
            str[index--] = '%';
        } else {
            str[index--] = str[i];
        }
    }
}
```
