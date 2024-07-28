# Question

Given the `head` of a singly linked list, return _the middle node of the linked list_.

If there are two middle nodes, return **the second middle** node.

## Leetcode Link

[876. Middle of the Linked List](https://leetcode.com/problems/middle-of-the-linked-list/)

## Intuition & Approaches

To find the middle node of a linked list, we can use the **Two Pointers** approach. This approach uses two pointers, `slow` and `fast`, to traverse the linked list. The `slow` pointer moves one step at a time, while the `fast` pointer moves two steps at a time. When the `fast` pointer reaches the end of the list, the `slow` pointer will be pointing at the middle node of the linked list. If the number of nodes in the linked list is even, the `slow` pointer will be pointing at the second middle node. If in case we want the first middle node, we can initialize `fast` to `head.next` instead of `head`. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

Another approach is to count the number of nodes in the linked list in the first pass and then traverse the list again to find the middle node. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java

```java
class Solution {
    public ListNode middleNode(ListNode head) {
        ListNode fast = head;
        ListNode slow = head;

        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        return slow;
    }
}
```
