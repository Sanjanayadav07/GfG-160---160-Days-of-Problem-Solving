---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Tree
  - Binary Search Tree
---

#  _Day 14. Lowest Common Ancestor in a BST_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/lowest-common-ancestor-in-a-bst)

## 💡 **Problem Description:**

Given a **Binary Search Tree (BST)** with **unique values** and two nodes `n1` and `n2` (where `n1 != n2`), find the **Lowest Common Ancestor (LCA)** of the two given nodes in the BST.

The **LCA** is the lowest node in the BST that has both `n1` and `n2` as **descendants** (a node is also considered its own descendant).

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
        5
       / \
      4   6
     /     \
    3       7
             \
              8
```

`n1 = 7`, `n2 = 8`

<img src="https://github.com/user-attachments/assets/5bafc3f7-5c2c-423f-bc9e-53e3778a06ae" width="30%">

#### **Output:**

```
7
```

#### **Explanation:**

The lowest common ancestor of `7` and `8` is `7` itself.

### **Example 2:**

#### **Input:**

```
         20
        /  \
       8    22
      / \
     4   12
        /  \
       10  14
```

`n1 = 8`, `n2 = 14`

<img src="https://github.com/user-attachments/assets/c6c5010f-c136-40ab-97ef-a275ad006aa3" width="30%">

#### **Output:**

```
8
```

#### **Explanation:**

`8` is the lowest node that is an ancestor of both `8` and `14`.

### **Example 3:**

#### **Input:**

```
    2
   / \
  1   3
```

`n1 = 1`, `n2 = 3`

<img src="https://github.com/user-attachments/assets/80b0cf12-510e-4154-a4af-b988859c239b" width="30%">

#### **Output:**

```
2
```

#### **Explanation:**

`2` is the lowest node that is an ancestor of both `1` and `3`.

### **Constraints:**

- $\(1 \leq \text{Number of Nodes} \leq 10^5\)$
- $\(1 \leq \text{node->data} \leq 10^5\)$
- $\(1 \leq \text{Node Value}, n1, n2 \leq 10^5\)$

## 🎯 **My Approach:**

### **Iterative Approach (O(H) Time, O(1) Space)**

1. Start from the **root** of the BST.
2. If `root->data` is **greater than both** `n1` and `n2`, move to the **left subtree**.
3. If `root->data` is **smaller than both** `n1` and `n2`, move to the **right subtree**.
4. Otherwise, return `root` as it is the **Lowest Common Ancestor (LCA)**.

### **Algorithm Steps:**

1. Start at the **root node**.
2. While `root` is not `NULL`:
   - If `root->data > max(n1, n2)`, move **left**.
   - If `root->data < min(n1, n2)`, move **right**.
   - Otherwise, **root is the LCA**, return it.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(H)`, where `H` is the height of the BST. In a balanced BST, `H = log N`, so this is efficient.
- **Expected Auxiliary Space Complexity:** `O(1)`, as no additional data structures are used.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    Node LCA(Node root, Node n1, Node n2) {
        while (root != null && (root.data > Math.max(n1.data, n2.data) || root.data < Math.min(n1.data, n2.data)))
            root = (root.data > n1.data) ? root.left : root.right;
        return root;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
