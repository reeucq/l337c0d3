# Question

Given a string `s`, reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.

## Leetcode Link

[557. Reverse Words in a String III](https://leetcode.com/problems/reverse-words-in-a-string-iii/)

## Approaches

1. **Iterate and Reverse**: We can split the array by spaces and then iterate over each word and reverse it. This approach has a time complexity of `O(n)` and a space complexity of `O(n)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public String reverseWords(String s) {
        String[] words = s.split(" ");
        StringBuffer sb = new StringBuffer();
        for(int i = 0; i < words.length - 1; i++) {
            sb.append(reverseWord(words[i]));
            sb.append(" ");
        }
        sb.append(reverseWord(words[words.length - 1]));
        return sb.toString();
    }

    private String reverseWord(String word) {
        char[] wordArr = word.toCharArray();
        int i = 0, j = wordArr.length - 1;
        while(i < j) {
            char temp = wordArr[i];
            wordArr[i] = wordArr[j];
            wordArr[j] = temp;
            i++;
            j--;
        }
        return new String(wordArr);
    }
}
```

### Java Approach 1 - Without Split

```java
class Solution {

    private void reverse(char[] chars, int left, int right){
        while ( left < right ){
            char ch = chars[left];
            chars[left] = chars[right];
            chars[right] = ch;

            right--;
            left++;
        }
    }

    public String reverseWords(String s) {

        char[] chars = s.toCharArray();

        int left  = 0;
        int right = 0;
        int n = s.length();

        while ( right < n ){

            if ( chars[right] == ' ' ){
                reverse(chars,left,right-1);
                left = right + 1;
            }

            right++;
        }

        reverse(chars,left,right-1);

        return new String(chars);
    }
}
```
