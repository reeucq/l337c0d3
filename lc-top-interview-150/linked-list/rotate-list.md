# Question

Given the `head` of a linked list, rotate the list to the right by `k` places.

## Leetcode Link

[61. Rotate List](https://leetcode.com/problems/rotate-list/)

## Approach

The algorithm first calculates the length of the list, then adjusts k to handle cases where k is larger than the list length. It then finds the new tail node by traversing (length - k - 1) steps from the head. Finally, it performs the rotation by breaking the list at the new tail, connecting the original tail to the original head, and returning the new head. This has a time complexity of $O(n)$ and a space complexity of $O(1)$.

## Solutions

### Java

```java
class Solution {
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null || k == 0) {
            return head;
        }

        // Calculate the length of the list
        int length = 0;
        ListNode current = head;
        while (current != null) {
            current = current.next;
            length++;
        }

        // Adjust k if it's larger than the list length
        k = k % length;
        if (k == 0) {
            return head;
        }

        // Find the new tail node
        current = head;
        for (int i = 0; i < length - k - 1; i++) {
            current = current.next;
        }

        // Perform the rotation
        ListNode newHead = current.next;
        current.next = null;
        ListNode newTail = newHead;
        while (newTail.next != null) {
            newTail = newTail.next;
        }
        newTail.next = head;

        return newHead;
    }
}
```
