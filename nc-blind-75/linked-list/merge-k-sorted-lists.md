# Question

You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

_Merge all the linked-lists into one sorted linked-list and return it._

## Leetcode Link

[23. Merge k Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)

## Approaches

1. **Priority Queue**: We can use a priority queue to store the heads of all the linked lists. We can add the heads of all the linked lists to the priority queue. We can then remove the smallest element from the priority queue and add it to the result linked list. We can then add the next element from the linked list of the removed element to the priority queue. We can repeat this process until the priority queue is empty. This approach has a time complexity of `O(n log k)`, where `n` is the total number of elements in all the linked lists and `k` is the number of linked lists and a space complexity of `O(k)`.

2. **Divide and Conquer**: We can divide the linked lists into two halves and merge the two halves. We can then merge the merged linked lists with the next half. We can repeat this process until we have merged all the linked lists. This approach has a time complexity of `O(n log k)` and a space complexity of `O(log k)`.

## Solutions

### Java Approach 1

```java
class Solution {
    public ListNode mergeKLists(ListNode[] lists) {
        PriorityQueue<ListNode> pq = new PriorityQueue<>((a,b) -> a.val - b.val);
        for(ListNode list : lists) if(list != null) pq.offer(list);

        ListNode dummy = new ListNode(0);
        ListNode res = dummy;

        while(pq.size() > 0) {
            ListNode node = pq.poll();
            res.next = node;
            res = res.next;
            if(node.next != null) pq.offer(node.next);
        }

        return dummy.next;
    }
}
```

### Java Approach 2

```java
public List<Integer> mergeKListsDivideAndConquer(List<List<Integer>> lists) {
    if (lists == null || lists.size() == 0) {
        return new ArrayList<>();
    }
    return mergeHelper(lists, 0, lists.size() - 1);
}

private List<Integer> mergeHelper(List<List<Integer>> lists, int left, int right) {
    if (left == right) {
        return lists.get(left);
    }
    int mid = left + (right - left) / 2;
    List<Integer> l1 = mergeHelper(lists, left, mid);
    List<Integer> l2 = mergeHelper(lists, mid + 1, right);
    return mergeTwoLists(l1, l2);
}

private List<Integer> mergeTwoLists(List<Integer> l1, List<Integer> l2) {
    List<Integer> merged = new ArrayList<>();
    int i = 0, j = 0;
    while (i < l1.size() && j < l2.size()) {
        if (l1.get(i) < l2.get(j)) {
            merged.add(l1.get(i++));
        } else {
            merged.add(l2.get(j++));
        }
    }
    while (i < l1.size()) {
        merged.add(l1.get(i++));
    }
    while (j < l2.size()) {
        merged.add(l2.get(j++));
    }
    return merged;
}

```
