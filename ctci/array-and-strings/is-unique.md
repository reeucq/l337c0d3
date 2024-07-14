# Question

Implement an algorithm to determine if a string has all unique characters.

## Approaches

1. **Brute Force**: We can use a nested loop to compare each character with every other character in the string. If we find any duplicate characters, we return false. This approach has a time complexity of $O(n^2)$ and a space complexity of $O(1)$.

2. **Use Extra Space to Store the State of Characters**: We can use an additional data structure like a boolean array or a hash set to keep track of the characters we have seen so far. If we encounter a character that is already present in the data structure, we return false. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

3. **Bit Manipulation**: We can use a bit vector to represent the state of characters. We initialize a bit vector with 0 and set the bit corresponding to the character's ASCII value to 1. If we encounter a character whose bit is already set, we return false. This approach has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Brute Force

```java
public boolean isUnique(String str) {
    for (int i = 0; i < str.length(); i++) {
        for (int j = i + 1; j < str.length(); j++) {
            if (str.charAt(i) == str.charAt(j)) {
                return false;
            }
        }
    }
    return true;
}
```

### Use Extra Space to Store the State of Characters

```java
public boolean isUnique(String str) {
    boolean[] charSet = new boolean[128];
    for (int i = 0; i < str.length(); i++) {
        int val = str.charAt(i);
        if (charSet[val]) {
            return false;
        }
        charSet[val] = true;
    }
    return true;
}
```

### Bit Manipulation

```java
public boolean isUnique(String str) {
    int checker = 0;
    for (int i = 0; i < str.length(); i++) {
        int val = str.charAt(i) - 'a';
        if ((checker & (1 << val)) > 0) {
            return false;
        }
        checker |= (1 << val);
    }
    return true;
}
```
