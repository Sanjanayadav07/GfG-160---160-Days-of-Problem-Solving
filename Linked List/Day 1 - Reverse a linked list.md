---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Linked-List
---

#  _Day 1. Reverse a linked list_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/linked-list-gfg-160/problem/reverse-a-linked-list)

## 💡 **Problem Description:**

You are given the head of a singly linked list. Your task is to reverse the list and return the reversed head.

## 🔍 **Example Walkthrough:**

**Input:**  
`head: 1 -> 2 -> 3 -> 4 -> NULL`  
**Output:**  
`head: 4 -> 3 -> 2 -> 1 -> NULL`

**Explanation:** <br/>
<img src="https://github.com/user-attachments/assets/cbbb7094-9d12-4b42-98c8-8fe47af1bbb8" width="45%"><br/>

**Input:**  
`head: 2 -> 7 -> 10 -> 9 -> 8 -> NULL`  
**Output:**  
`head: 8 -> 9 -> 10 -> 7 -> 2 -> NULL`

**Explanation:** <br/>
<img src="https://github.com/user-attachments/assets/3404169a-bd59-4534-b9c0-2b31a9d9631e" width="50%"><br/>

**Input:**  
`head: 10 -> NULL`  
**Output:**  
`head: 10 -> NULL`

**Explanation:** <br/>
<img src="https://github.com/user-attachments/assets/e401ab9b-d5a9-474d-80c7-7e9c5389db40" width="30%"><br/>

### Constraints:

- 1 <= number of nodes, data of nodes <= $10^5$

## 🎯 **My Approach:**

1. **Iterative Reversal Algorithm**:  
   The problem can be efficiently solved using an iterative approach by traversing the linked list and reversing the `next` pointers of each node.

   - Start with two pointers: `prev` (initialized to `NULL`) and `current` (initialized to the head of the list).
   - In each iteration, update the `next` pointer of the `current` node to point to the `prev` node, then move `prev` and `current` forward.
   - Continue the process until the entire list is reversed.

2. **Steps:**
   - Initialize `prev` to `NULL` and `current` to the head of the list.
   - Traverse the list while `current` is not `NULL`.
   - For each node, reverse the `next` pointer to point to `prev`.
   - Move the `prev` and `current` pointers one step forward.
   - Once the list is completely reversed, return `prev` as the new head.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n), where `n` is the number of nodes in the linked list. We traverse the entire list once.
- **Expected Auxiliary Space Complexity:** O(1), as we only use a constant amount of additional space (for the `prev` and `current` pointers).

## 📝 **Solution Code**

#### Example Walkthrough:

Let the initial linked list be: $\(1 \rightarrow 2 \rightarrow 3 \rightarrow \text{nullptr}\)$

1. **Initialization**: `prev = nullptr`, `head = 1`
2. **First Iteration**:
   - Swap `head->next` and `prev`: Now `1->next = nullptr`
   - Swap `head` and `prev`: `prev = 1`, `head = 2`
3. **Second Iteration**:
   - Swap `head->next` and `prev`: Now `2->next = 1`
   - Swap `head` and `prev`: `prev = 2`, `head = 3`
4. **Third Iteration**:
   - Swap `head->next` and `prev`: Now `3->next = 2`
   - Swap `head` and `prev`: `prev = 3`, `head = nullptr`
5. **Termination**:
   - `head` is `nullptr`, and `prev` points to the reversed list: $\(3 \rightarrow 2 \rightarrow 1 \rightarrow \text{nullptr}\)$

</details>

## Code (Java)

```java
class Solution {
    Node reverseList(Node head) {
        Node prev = null;
        while (head != null) {
            Node next = head.next;
            head.next = prev;
            prev = head;
            head = next;
        }
        return prev;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
