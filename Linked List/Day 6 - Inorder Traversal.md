---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 6. Inorder Traversal_

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/inorder-traversal)

## 💡 **Problem Description:**

Given a Binary Tree, your task is to return its In-Order Traversal.

An inorder traversal first visits the left subtree (including its entire subtree), then visits the node, and finally visits the right subtree (including its entire subtree).

## 🔍 **Example Walkthrough:**

- **Example 1:**

- **Input:** `root[] = [1, 2, 3, 4, 5]`

<img src="https://github.com/user-attachments/assets/7733cb99-7571-4602-b46d-4293412d4b7e" width="40%">

- **Output:** `[4, 2, 5, 1, 3]`
- **Explanation:** The in-order traversal of the given binary tree is `[4, 2, 5, 1, 3]`.

- **Example 2:**

- **Input:** `root[] = [8, 1, 5, N, 7, 10, 6, N, 10, 6]`

<img src="https://github.com/user-attachments/assets/a4f35d5c-2197-4bf3-af03-ef52d57bed50" width="40%">

- **Output:** `[1, 7, 10, 8, 6, 10, 5, 6]`
- **Explanation:** The in-order traversal of the given binary tree is `[1, 7, 10, 8, 6, 10, 5, 6]`.

## 🎯 **My Approach:**

1. **Recursive In-Order Traversal:**

   - **Visit Left Subtree:** Recursively traverse the left subtree.
   - **Process Current Node:** Once the left subtree is completely traversed, record the current node's data.
   - **Visit Right Subtree:** Recursively traverse the right subtree.

2. **Storing the Result:**

   - As each node is processed, add its data to a list (or array).
   - Return the list after completing the traversal.

3. **Handling Null Nodes:**
   - If a node is `null` (or `None` in Python), simply return without performing any action.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n), where n is the number of nodes in the binary tree, since every node is visited exactly once.
- **Expected Auxiliary Space Complexity:** O(1) in the worst case due to the recursion stack in a skewed tree. In a balanced tree, the recursion stack space is O(log n).

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    ArrayList<Integer> inOrder(Node r) {
        ArrayList<Integer> a = new ArrayList<>();
        f(r, a);
        return a;
    }
    void f(Node r, ArrayList<Integer> a) {
        if (r == null) return;
        f(r.left, a);
        a.add(r.data);
        f(r.right, a);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
