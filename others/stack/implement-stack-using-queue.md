# Question

Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (`push`, `top`, `pop`, and `empty`).

Implement the MyStack class:

- `void push(int x)` Pushes element x to the top of the stack.
- `int pop()` Removes the element on the top of the stack and returns it.
- `int top()` Returns the element on the top of the stack.
- `boolean empty()` Returns true if the stack is empty, false otherwise.

## Leetcode Link

[225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)

## Approaches

1. Use a queue and whenever a new element arrives, move all the elements before the new element to the back of the queue. This way, the new element will be at the front of the queue, and the rest of the elements will be in the same order as they were before. This approach ensures that the top element is always at the front of the queue, and the rest of the elements are in the same order as they were before.
   - Time complexity: O(n) for push, O(1) for pop, O(1) for top, O(1) for empty
   - Space complexity: O(n)

## Solutions

### Java Approach 1

```java
class MyStack {

    Queue<Integer> q;

    public MyStack() {
        q = new LinkedList<>();
    }

    public void push(int x) {
        q.add(x);
        for(int i = 0; i < q.size() - 1; i++) {
            int temp = q.poll();
            q.add(temp);
        }
    }

    public int pop() {
        return q.poll();
    }

    public int top() {
        return q.peek();
    }

    public boolean empty() {
        return q.isEmpty();
    }
}
```
