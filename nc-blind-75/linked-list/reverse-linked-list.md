# Question

Given the `head` of a singly linked list, reverse the list, and return the reversed list.

## Leetcode Link

[206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

## Approaches

1. **Iterative**: Initialize three pointers, prev, current and next. Iterate through the list - save next node, reverse the link, move forward, and then set the new head to prev. Return prev. This has a time complexity of O(n) and space complexity of O(1).

2. **Recursive**: Base Case: If the list is empty and has only one node, return the head. Recursive Case: Call the function recusrively on the rest of the list, set the node next pointer to the current node, set the current node next pointer to null. Return the new head (which will be the last node of the original list)

## Solutions

### Java Approach 1

```java
public ListNode reverseListIterative(ListNode head) {
    ListNode prev = null;
    ListNode current = head;
    ListNode next = null;

    while (current != null) {
        next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }

    return prev;
}
```

### Java Approach 2

```java
public ListNode reverseListRecursive(ListNode head) {
    if (head == null || head.next == null) {
        return head;
    }

    ListNode rest = reverseListRecursive(head.next);
    head.next.next = head;
    head.next = null;

    return rest;
}
```
