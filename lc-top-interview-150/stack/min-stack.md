# Question

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

- `MinStack()` initializes the stack object.
- `void push(int val)` pushes the element `val` onto the stack.
- `void pop()` removes the element on the top of the stack.
- `int top()` gets the top element of the stack.
- `int getMin()` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.

## Leetcode Link

[155. Min Stack](https://leetcode.com/problems/min-stack/)

## Approaches

1. **Using Two Stacks**: We can use two stacks to keep track of the elements and the minimum element at each step. The first stack will store the elements, and the second stack will store the minimum element at each step. When pushing an element onto the stack, we can check if it is less than or equal to the current minimum element. If it is, we can push it onto the second stack as well. When popping an element from the stack, we can check if it is equal to the current minimum element. If it is, we can pop it from the second stack as well. This approach requires `O(n)` extra space.

2. **Using a Linked List**: We can use a linked list to keep track of the elements and the minimum element at each step. Each node in the linked list will store the element and the minimum element at that step. When pushing an element onto the stack, we can check if it is less than or equal to the current minimum element. If it is, we can update the minimum element. When popping an element from the stack, we can update the minimum element to the minimum element at the previous step. This approach requires `O(n)` extra space.

## Solutions

### Java Approach 1

```java
class MinStack {
    private Stack<Integer> stack;
    private Stack<Integer> minStack;

    public MinStack() {
        stack = new Stack<>();
        minStack = new Stack<>();
    }

    public void push(int val) {
        stack.push(val);
        if (minStack.isEmpty() || val <= minStack.peek()) {
            minStack.push(val);
        }
    }

    public void pop() {
        if (!stack.isEmpty()) {
            if (stack.peek().equals(minStack.peek())) {
                minStack.pop();
            }
            stack.pop();
        }
    }

    public int top() {
        if (!stack.isEmpty()) {
            return stack.peek();
        }
        throw new EmptyStackException();
    }

    public int getMin() {
        if (!minStack.isEmpty()) {
            return minStack.peek();
        }
        throw new EmptyStackException();
    }
}
```

### Java Approach 2

```java
import java.util.EmptyStackException;

public class MinStack {
    private Node top;

    private class Node {
        int value;
        int min;
        Node next;

        Node(int value, int min) {
            this.value = value;
            this.min = min;
        }
    }

    public MinStack() {
        top = null;
    }

    public void push(int x) {
        if (top == null) {
            top = new Node(x, x);
        } else {
            Node newNode = new Node(x, Math.min(x, top.min));
            newNode.next = top;
            top = newNode;
        }
    }

    public void pop() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        top = top.next;
    }

    public int top() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return top.value;
    }

    public int getMin() {
        if (isEmpty()) {
            throw new EmptyStackException();
        }
        return top.min;
    }

    public boolean isEmpty() {
        return top == null;
    }
}
```
