---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Tree
  - Binary Search Tree
---

# 🚀 _Day 10. Check for BST_ 🧠

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/check-for-bst)

## 💡 **Problem Description:**

Given the root of a binary tree, check whether it is a **Binary Search Tree (BST)** or not.

### **Definition of BST:**

- The **left subtree** of a node contains only nodes with keys **less than** the node's key.
- The **right subtree** of a node contains only nodes with keys **greater than** the node's key.
- **Both** the left and right subtrees must also be binary search trees.
- **Note:** BSTs **cannot contain duplicate nodes**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

`root = [2, 1, 3, N, N, N, 5]`

<img src="https://github.com/user-attachments/assets/c5eba8ff-c2eb-4000-82d6-1358f3548d87" width="30%">

#### **Output:**

```
true
```

#### **Explanation:**

- The left subtree of every node contains smaller keys and right subtree of every node contains greater keys.
  Hence, **it is a BST**.

### **Example 2:**

#### **Input:**

`root = [2, N, 7, N, 6, N, 9] `

<img src="https://github.com/user-attachments/assets/f45825cc-46bf-421c-825e-f0522f68a7f3" width="30%">

#### **Output:**

```
false
```

#### **Explanation:**

- Since the node to the right of node with key `7` has lesser key value,  
  Hence, **it is not a BST**.

### **Example 3:**

#### **Input:**

`root = [10, 5, 20, N, N, 9, 25]`

<img src="https://github.com/user-attachments/assets/cc8b90e4-c498-4448-957d-617f59a1d219" width="30%">

#### **Output:**

```
false
```

#### **Explanation:**

- The node with key `9` present in the right subtree has lesser key value than root node.  
  Hence, **it is not a BST**.

## **Constraints:**

- 1 ≤ Number of nodes ≤ $10^5$
- 1 ≤ node->data ≤ $10^9$

## 🎯 **My Approach:**

### ✅ **Min–Max Recursion (Top-Down Approach)**

1. **Base Case:**

   - If the current node is `NULL`, return `true` (an empty tree is a valid BST).

2. **Check Current Node:**

   - The current node’s value should be **greater than the `min` value** and **less than the `max` value**.

3. **Recursive Calls:**

   - Recursively check the left subtree with the updated range `[min, node->data]`.
   - Recursively check the right subtree with the updated range `[node->data, max]`.

4. **Return Result:**
   - The tree is a BST only if **both left and right subtrees** are BSTs.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)` We visit each node **exactly once**, performing constant-time operations at each step.
- **Expected Auxiliary Space Complexity:** `O(H)` Due to the recursion stack, where `H` is the **height of the tree**. In the worst case (skewed tree), `H = N`. In the best case (balanced tree), `H = log N`.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    boolean isBST(Node root) {
        return isBST(root, Integer.MIN_VALUE, Integer.MAX_VALUE);
    }

    boolean isBST(Node node, int min, int max) {
        return node == null || (node.data > min && node.data < max &&
                isBST(node.left, min, node.data) &&
                isBST(node.right, node.data, max));
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
