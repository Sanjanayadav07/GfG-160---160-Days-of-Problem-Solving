---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 4. Mirror Tree_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/mirror-tree)

## 💡 **Problem Description:**

Given a binary tree, convert it into its **Mirror Tree** by swapping the left and right children of all non-leaf nodes.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
        1
       / \
      2   3
         /
        4
```

#### **Output:**

```
        1
       / \
      3   2
       \
        4
```

<img src="https://github.com/user-attachments/assets/16c6b8d7-160f-4260-b6e5-629d51b3d248" width="40%">

#### **Explanation:**

Every non-leaf node has its left and right children interchanged.

### **Example 2:**

#### **Input:**

```
        1
       / \
      2   3
     / \
    4   5
```

#### **Output:**

```
        1
       / \
      3   2
         / \
        5   4
```

<img src="https://github.com/user-attachments/assets/f4d620f5-19e1-4c84-94a5-a543cb89f9d1" width="40%">

#### **Explanation:**

Every non-leaf node has its left and right children interchanged.

### **Constraints:**

- 1 ≤ number of nodes ≤ $10^5$
- 1 ≤ node->data ≤ $10^5$

## 🎯 **My Approach:**

### **Recursive DFS (Top-Down)**

1. **Base Case:** If the node is `NULL`, return.
2. **Recursively traverse** the left and right subtrees.
3. **Swap** the left and right children of the current node.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, since every node is visited once.
- **Expected Auxiliary Space Complexity:** `O(1)` OR `O(H)` for recursive DFS (`H = height of the tree`).

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    void mirror(Node node) {
        if (node == null) return;
        mirror(node.left);
        mirror(node.right);
        Node temp = node.left;
        node.left = node.right;
        node.right = temp;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐


---
