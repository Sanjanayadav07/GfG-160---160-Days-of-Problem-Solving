---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Stack
---

#  _Day 7. Get Min from Stack_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/stack-gfg-160/problem/get-minimum-element-from-stack)

## 💡 **Problem Description:**

Implement a stack that supports the following operations in **O(1) time**:

- `push(x)`: Push an integer **x** onto the stack.
- `pop()`: Remove the top element from the stack.
- `peek()`: Return the top element of the stack. If empty, return `-1`.
- `getMin()`: Retrieve the **minimum element** in the stack. If empty, return `-1`.

## 🔍 **Example Walkthrough:**

#### **Example 1**

**Input:**

```
q = 7
queries = [[1, 2], [1, 3], [3], [2], [4], [1, 1], [4]]
```

**Output:**

```
[3, 2, 1]
```

**Explanation:**

```
push(2) -> Stack: [2]
push(3) -> Stack: [2, 3]
peek() -> 3
pop() -> Stack: [2]
getMin() -> 2
push(1) -> Stack: [2, 1]
getMin() -> 1
```

#### **Example 2**

**Input:**

```
q = 4
queries = [[1, 4], [1, 2], [4], [3]]
```

**Output:**

```
[2, 2]
```

**Explanation:**

```
push(4) -> Stack: [4]
push(2) -> Stack: [4, 2]
getMin() -> 2
peek() -> 2
```

### **Constraints**

- $\(1 \leq q \leq 10^5\)$ (Number of queries)
- $\(1 \leq x \leq 10^9\)$ (Stack elements are within this range)

## 🎯 **My Approach:**

### **Using Two Stacks (O(1) Time, O(N) Space)**

1. Use **two stacks**:
   - `s` → **Normal stack** for elements.
   - `minStack` → **Keeps track of minimum values**.
2. When pushing an element `x`, check:
   - If `minStack` is empty or `x <= minStack.top()`, push `x` into `minStack`.
3. While popping, if the popped element is the **current min**, pop from `minStack`.
4. `getMin()` always returns `minStack.top()`.

## 🕒 **Time and Auxiliary Space Complexity**

| **Operation** | **Time Complexity** | **Space Complexity** |
| ------------- | ------------------- | -------------------- |
| `push(x)`     | O(1)                | O(N) (extra stack)   |
| `pop()`       | O(1)                | O(N) (extra stack)   |
| `peek()`      | O(1)                | O(1)                 |
| `getMin()`    | O(1)                | O(1)                 |

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    private Stack<Integer> s = new Stack<>();
    private Stack<Integer> minStack = new Stack<>();
    public void push(int x) {
        s.push(x);
        if (minStack.isEmpty() || x <= minStack.peek()) {
            minStack.push(x);
        }
    }
    public void pop() {
        if (!s.isEmpty()) {
            if (s.peek().equals(minStack.peek())) {
                minStack.pop();
            }
            s.pop();
        }
    }
    public int peek() {
        return s.isEmpty() ? -1 : s.peek();
    }
    public int getMin() {
        return minStack.isEmpty() ? -1 : minStack.peek();
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
