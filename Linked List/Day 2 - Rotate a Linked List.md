---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Linked-List
---

#  _Day 2. Rotate a linked list_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/linked-list-gfg-160/problem/rotate-a-linked-list)

## 💡 **Problem Description:**

You are given the head of a singly linked list and an integer `k`. Your task is to left-rotate the linked list `k` times.

## 🔍 **Example Walkthrough:**

**Input:**  
`head = 10 -> 20 -> 30 -> 40 -> 50`, `k = 4`  
**Output:**  
`50 -> 10 -> 20 -> 30 -> 40`  
**Explanation:**  
Rotate 1: `20 -> 30 -> 40 -> 50 -> 10`  
Rotate 2: `30 -> 40 -> 50 -> 10 -> 20`  
Rotate 3: `40 -> 50 -> 10 -> 20 -> 30`  
Rotate 4: `50 -> 10 -> 20 -> 30 -> 40`

<img src="https://github.com/user-attachments/assets/45c9ddf0-6231-4d56-99c7-2f008defa00a" width="50%">

**Input:**  
`head = 10 -> 20 -> 30 -> 40`, `k = 6`  
**Output:**  
`30 -> 40 -> 10 -> 20`  
**Explanation:** <br/>
Since `k = 6` exceeds the length of the list (`4`), `k` is reduced to `k % length = 2`. After two left rotations:  
`10 -> 20 -> 30 -> 40` → `20 -> 30 -> 40 -> 10` → `30 -> 40 -> 10 -> 20`.
<br/>

<img src="https://github.com/user-attachments/assets/1759b1e9-f5a5-4c2b-9da9-17aba6ea7ab1" width="50%">

### Constraints:

- $`1 <= number of nodes <= 10^5`$
- $`0 <= k <= 10^9`$
- $`0 <= data of node <= 10^9`$

## 🎯 **My Approach:**

1. **Key Observations:**

   - If `k` is greater than the length of the list, we only need to perform `k % length` rotations, as rotating the list `length` times results in the same list.
   - Breaking the linked list into two parts and re-linking the tail to the head helps achieve the rotation efficiently.

2. **Algorithm:**
   - Compute the length of the list (`len`).
   - Reduce `k` to `k % len` to handle large values of `k`.
   - If `k = 0`, return the original list as no rotation is required.
   - Traverse the list to find the new tail (the node at position `len - k`) and the new head (the node at position `len - k + 1`).
   - Break the list into two parts by setting the `next` pointer of the new tail to `nullptr`.
   - Re-link the old tail to the original head.
   - Return the new head.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n), where `n` is the length of the linked list. This is because we traverse the list twice: once to calculate its length and once to locate the new head and tail.
- **Expected Auxiliary Space Complexity:** O(1), as no additional space is used apart from a few pointers.

## 📝 **Solution Code**
## Code (Java)

```java
class Solution {
  public Node rotate(Node head, int k) {
    if (head == null || head.next == null || k == 0) return head;
    int len = 1;
    Node tail = head;
    while (tail.next != null) {
      tail = tail.next;
      len++;
    }
    k %= len;
    if (k == 0) return head;
    Node newTail = head;
    for (int i = 1; i < k; i++) {
      newTail = newTail.next;
    }
    Node newHead = newTail.next;
    newTail.next = null;
    tail.next = head;
    return newHead;
  }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
