# Question
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

## Leetcode Link
[242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

## Approaches
1. **Sorting**: Change both strings to character arrays, sort them and compare them. Time complexity is $O(nlogn)$ and space complexity is $O(n)$.
2. **Hashing**: Convert both strings to hashmap with character frequency and compare them. Time complexity is $O(n)$ and space complexity is $O(n)$.
3. An alternative strategy is to count the number of occurrences of each character in our inputs. If these histograms are equal between the inputs, then the strings are anagrams. To save a little memory, let’s build only one histogram. We’ll increment the counts for each character in the first string, and decrement the count for each character in the second. If the two strings are anagrams, then the result will be that everything balances to 0. Time complexity is $O(n)$ and space complexity is $O(1)$.

## Solutions
### Java Approach 2
```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if(s.length() != t.length())
            return false;
        
        HashMap<Character, Integer> hm1 = new HashMap<>();
        HashMap<Character, Integer> hm2 = new HashMap<>();

        for(int i = 0; i < s.length(); i++) {
            hm1.put(s.charAt(i), hm1.getOrDefault(s.charAt(i), 0) + 1);
            hm2.put(t.charAt(i), hm2.getOrDefault(t.charAt(i), 0) + 1);
        }

        return hm1.equals(hm2);
    }
}
```

### Java Approach 3
Note: If all characters are allowed rather than only lowercase ones, then we can change the length of store to 256 and we don't have to minus `a` from the character.

```Java
class Solution {
    public boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) return false;
        int[] store = new int[26];

        for (int i = 0; i < s.length(); i++) {
            store[s.charAt(i) - 'a']++;
            store[t.charAt(i) - 'a']--;
        }

        for (int n : store) if (n != 0) return false;

        return true;
    }
}
```

### Javascript Approach 1
```Javascript
function isAnagram(s, t) {
    if (s.length !== t.length) return false;
    return 
    s.split('').sort().join('') === t.split('').sort().join('');
}
```

### Python Approach 1
```Python
def is_anagram(s, t):
    if len(s) != len(t):
        return False
    return sorted(s) == sorted(t)
```
