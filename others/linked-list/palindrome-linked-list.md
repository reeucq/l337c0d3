# Question

Given the `head` of a singly linked list, return _`true` if it is a palindrome or false otherwise._

## Leetcode Link

[234. Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)

## Approaches

1. Reverse the Second Half

   - Reverse the second half of the linked list and compare it with the first half.
   - Time complexity: O(n)
   - Space complexity: O(1)

2. Using Extra Space
   - Store the values of the linked list in an string / array and check if it is a palindrome.
   - Time complexity: O(n)
   - Space complexity: O(n)

## Solutions

### Java Approach 1

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        if (head == null || head.next == null) return true;

        // Find the middle of the list
        ListNode slow = head;
        ListNode fast = head;
        while (fast.next != null && fast.next.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // Reverse the second half of the list
        ListNode secondHalf = reverseList(slow.next);

        // Compare the first half with the reversed second half
        ListNode firstHalf = head;
        while (secondHalf != null) {
            if (firstHalf.val != secondHalf.val) {
                return false;
            }
            firstHalf = firstHalf.next;
            secondHalf = secondHalf.next;
        }

        return true;
    }

    private ListNode reverseList(ListNode head) {
        ListNode prev = null;
        ListNode current = head;
        while (current != null) {
            ListNode nextTemp = current.next;
            current.next = prev;
            prev = current;
            current = nextTemp;
        }
        return prev;
    }
}
```

### Java Approach 2

```java
class Solution {
    public boolean isPalindrome(ListNode head) {
        StringBuilder sb = new StringBuilder(10001);
        ListNode cur = head;
        while(cur != null) {
            sb.append(cur.val);
            cur = cur.next;
        }
        return sb.toString().equals(sb.reverse().toString());
    }
}
```
