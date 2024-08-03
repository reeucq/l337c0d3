# Question

Given the `head` of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return _the reordered list._

## Leetcode Link

[328. Odd Even Linked List](https://leetcode.com/problems/odd-even-linked-list/)

## Approaches

1. **Iterative**: We can iterate over the linked list and keep track of the odd and even nodes. We'll maintain two pointers, one for the odd nodes and one for the even nodes. We'll then connect the odd nodes to the even nodes. This approach has a time complexity of `O(n)` and a space complexity of `O(1)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode oddEvenList(ListNode head) {
        ListNode dummy = new ListNode(Integer.MIN_VALUE,head);
        ListNode odds = new ListNode(0);
        ListNode oddList = odds;
        ListNode evens = new ListNode(0);
        ListNode evensList = evens;
        ListNode cur = head;
        int count = 1;

        while(cur != null) {
            if(count % 2 == 1) {
                oddList.next = cur;
                oddList = oddList.next;
            } else {
                evensList.next = cur;
                evensList = evensList.next;
            }
            count++;
            cur = cur.next;
        }
        evensList.next = null;
        oddList.next = evens.next;
        return odds.next;
    }
}
```

### Java Approach 1 - More Readable & Elegant

```java
public class Solution {
public ListNode oddEvenList(ListNode head) {
    if (head != null) {

        ListNode odd = head, even = head.next, evenHead = even;

        while (even != null && even.next != null) {
            odd.next = odd.next.next;
            even.next = even.next.next;
            odd = odd.next;
            even = even.next;
        }
        odd.next = evenHead;
    }
    return head;
}}
```
