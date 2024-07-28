# Question

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

## Leetcode Link

[19. Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

## Approaches

1. **Two Pass**: Count the length of the linked list in the first pass. Then, remove the `n-th` node from the beginning of the list in the second pass.

2. **Two Pointers**: Maintain two pointers, fast and slow, and move them n steps apart. Then, move both pointers one step at a time until the fast pointer reaches the end of the list. The slow pointer will be pointing at the `n-th` node from the end of the list.

## Solutions

### Java Approach 1

```java
public static Node DeleteNthNodefromEnd(Node head, int N) {
    if (head == null) {
        return null;
    }
    int cnt = 0;
    Node temp = head;

    // Count the number of nodes in the linked list
    while (temp != null) {
        cnt++;
        temp = temp.next;
    }

    // If N equals the total number of nodes, delete the head
    if (cnt == N) {
        Node newhead = head.next;
        head = null;
        return newhead;
    }

    // Calculate the position of the node to delete (res)
    int res = cnt - N;
    temp = head;

    // Traverse to the node just before the one to delete
    while (temp != null) {
        res--;
        if (res == 0) {
            break;
        }
        temp = temp.next;
    }

    // Delete the Nth node from the end
    Node delNode = temp.next;
    temp.next = temp.next.next;
    delNode = null;
    return head;
}
```

### Java Approach 2

```java
class Solution {
    public ListNode removeNthFromEnd(ListNode head, int n) {
        ListNode dummy = new ListNode(0,head);
        ListNode slow = dummy, fast = dummy;

        while(n > 0) {
            fast = fast.next;
            n--;
        }

        while(fast.next != null) {
            fast = fast.next;
            slow = slow.next;
        }

        slow.next = slow.next.next;
        return dummy.next;
    }
}
```
