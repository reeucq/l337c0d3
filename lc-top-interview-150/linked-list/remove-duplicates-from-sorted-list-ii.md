# Question

Given the `head` of a sorted linked list, _delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list **sorted** as well._

## Leetcode Link

[82. Remove Duplicates From Sorted List II](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)

## Approach

1. Create a dummy node and point it to the head.
2. Create a pointer `prev` and point it to the dummy node.
3. Create a pointer `cur` and point it to the head.
4. Iterate through the list until `cur` & `cur.next` is not `NULL`
5. If `cur.val` is not equal to `cur.next.val`, then move `prev` and `cur` to the next node.
6. If `cur.val` is equal to `cur.next.val`, then move `cur` to the next node until `cur.val` is not equal to `cur.next.val`.
7. Set `prev.next` to `cur.next` and move `cur` to `cur.next`.
8. Return `dummy.next`.

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode deleteDuplicates(ListNode head) {
        ListNode dummy = new ListNode(-101,head);
        ListNode prev = dummy;
        ListNode cur = head;

        while(cur != null && cur.next != null) {
            if(cur.val != cur.next.val) {
                prev = cur;
                cur = cur.next;
            } else {
                while(cur != null && cur.next != null && cur.val == cur.next.val) {
                    cur = cur.next;
                }
                prev.next = cur.next;
                cur = cur.next;
            }
        }
        return dummy.next;
    }
}
```
