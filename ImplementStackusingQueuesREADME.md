# leet-day45

# LIFO Stack Using Two Queues

This C++ code demonstrates how to implement a Last-in-First-Out (LIFO) stack using two queues. The stack supports standard stack operations such as push, pop, top, and checking for emptiness.

## Implementation

The `MyStack` class uses two `std::queue` containers to simulate the stack behavior. The key idea is to efficiently maintain the LIFO property during the `push` operation using the two queues.

### `push` Operation

1. Transfer all elements from `q1` to `q2`.
2. Push the new element to `q1`.
3. Transfer all elements back from `q2` to `q1`.

### `pop` Operation

Pop the front element from `q1`.

### `top` Operation

Return the front element of `q1`.

### `empty` Operation

Check if `q1` is empty.

## Example

```cpp
#include <iostream>
#include <queue>

class MyStack {
private:
    std::queue<int> q1;
    std::queue<int> q2;

public:
    MyStack() {}

    void push(int x) {
        // Move all elements from q1 to q2
        while (!q1.empty()) {
            q2.push(q1.front());
            q1.pop();
        }

        // Push the new element to q1
        q1.push(x);

        // Move elements back from q2 to q1
        while (!q2.empty()) {
            q1.push(q2.front());
            q2.pop();
        }
    }

    int pop() {
        int topElement = q1.front();
        q1.pop();
        return topElement;
    }

    int top() {
        return q1.front();
    }

    bool empty() {
        return q1.empty();
    }
};

```

## Usage

1. Create an instance of the `MyStack` class.
2. Use the `push`, `pop`, `top`, and `empty` operations as needed.

## Complexity

- Push: O(n) (transfer between queues)
- Pop: O(1)
- Top: O(1)
- Empty: O(1)

The space complexity is O(n), where n is the number of elements in the stack.

## Follow-up

This implementation uses two queues. For the follow-up question of implementing the stack using only one queue, you can check other resources or examples as it can be a bit more complex.
