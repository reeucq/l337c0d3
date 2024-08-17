# Question

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

## Leetcode Link

[2. Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

## Intuition

We can add two numbers by iterating over the linked lists and adding the corresponding digits. We can keep track of the carry and add it to the next sum. We can create a dummy node to keep track of the head of the result linked list. We can then iterate over the linked lists and add the corresponding digits. We can then return the next of the dummy node.

## Solution

### Java

```java
class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummy = new ListNode(-1);
        ListNode res = dummy;
        int c = 0;

        while(l1 != null || l2 != null || c > 0) {
            int sum = c;

            if(l1 != null) {
                sum += l1.val;
                l1 = l1.next;
            }

            if(l2 != null) {
                sum += l2.val;
                l2 = l2.next;
            }

            c = sum / 10;
            sum = sum % 10;

            res.next = new ListNode(sum);
            res = res.next;
        }

        return dummy.next;
    }
}
```
