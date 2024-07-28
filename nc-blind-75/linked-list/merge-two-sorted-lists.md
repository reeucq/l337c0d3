# Question

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list._

## Leetcode Link

[21. Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

## Approaches

1. **Brute Force**: We can iterate over both the linked lists using two pointers and for each we check whether value in the first linked list is less than the value in the second linked list. If it is, then we add the node from the first linked list to the merged linked list and move the pointer to the next node. Otherwise, we add the node from the second linked list to the merged linked list and move the pointer to the next node. Once any of the one lists is exhausted, we can add the remaining nodes from the other linked list to the merged linked list. The time complexity of this approach is O(n) where n is the number of nodes in the shorter linked list and the space complexity is O(1).

## Solutions

### Java Approach 1 - Iterative

```java
class Solution {
    public ListNode mergeTwoLists(ListNode list1, ListNode list2) {
        if(list1 == null) return list2;
        if(list2 == null) return list1;

        ListNode dummy = new ListNode(0);
        ListNode merged = dummy;

        while(list1 != null && list2 != null) {
            if(list1.val < list2.val) {
                merged.next = list1;
                list1 = list1.next;
            } else {
                merged.next = list2;
                list2 = list2.next;
            }
            merged = merged.next;
        }

        merged.next = (list1 != null) ? list1 : list2;

        return dummy.next;
    }
}
```

### Java Approach 1 - Recursive

```java
public ListNode mergeTwoLists(ListNode l1, ListNode l2){
    if(l1 == null) return l2;
    if(l2 == null) return l1;
    if(l1.val < l2.val){
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else{
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
}
```
