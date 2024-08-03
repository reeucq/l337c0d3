# Question

You are given the head of a singly linked-list. The list can be represented as:

> L0 → L1 → … → Ln - 1 → Ln

_Reorder the list to be on the following form:_

> L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …

You may not modify the values in the list's nodes. Only nodes themselves may be changed.

## Leetcode Link

[143. Reorder List](https://leetcode.com/problems/reorder-list/)

## Approaches

1. **3-Step Approach**: This approach uses a three-step process to reorder the linked list. The first step is to find the middle node of the linked list. The second step is to reverse the second half of the linked list. The third step is to merge the first half of the linked list with the reversed second half.
   - Time complexity: O(n)
   - Space complexity: O(1)

## Solutions

### Java Approach 1

```java
class Solution {
    public void reorderList(ListNode head) {
        if(head == null || head.next == null) return;

        // find the middle of the linkedlist
        ListNode slow = head;
        ListNode fast = head;
        while(fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;
        }

        // divide ll into two parts
        ListNode middle = slow;
        ListNode rightList = reverse(middle.next);
        middle.next = null;
        ListNode leftList = head;

        // reorder the list
        ListNode cur1 = leftList;
        ListNode cur2 = rightList;
        ListNode res = new ListNode(0);

        while(cur1 != null || cur2 != null) {
            if(cur1 != null) {
                res.next = cur1;
                cur1 = cur1.next;
                res = res.next;
            }

            if(cur2 != null) {
                res.next = cur2;
                cur2 = cur2.next;
                res = res.next;
            }
        }

        head = res.next;
    }

    private ListNode reverse(ListNode head) {
        if(head == null || head.next == null) return head;

        ListNode cur = head;
        ListNode prev = null;

        while(cur != null) {
            ListNode temp = cur.next;
            cur.next = prev;
            prev = cur;
            cur = temp;
        }

        return prev;
    }
}
```
