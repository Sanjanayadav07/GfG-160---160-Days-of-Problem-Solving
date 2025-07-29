---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Tree
  - Binary Search Tree
---

#  _Day 13. Fixing Two nodes of a BST_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/fixed-two-nodes-of-a-bst)

## 💡 **Problem Description:**

Given the root of a **Binary Search Tree (BST)**, where exactly **two nodes were swapped** by mistake, your task is to **fix (or correct) the BST** by swapping them back. The **structure of the tree should not change**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
        10
       /  \
      5    8
     /  \
    2    20
```

<img src="https://github.com/user-attachments/assets/b3a4854c-a13c-49a4-89ec-f21dd98fbade" width="30%">

#### **Output:**

```
1
```

<img src="https://github.com/user-attachments/assets/eec53814-0d5d-4047-b24c-f4be44041eb7" width="30%">

#### **Explanation:**

The nodes **20 and 8** were swapped by mistake. After swapping them back, the BST is restored correctly.

### **Example 2:**

#### **Input:**

```
        5
       / \
     10   20
     / \
    2   8
```

<img src="https://github.com/user-attachments/assets/de261078-d5c2-4412-ae17-8afb5cf71937" width="30%">

#### **Output:**

```
1
```

<img src="https://github.com/user-attachments/assets/6f588971-07ab-4702-8e1b-4756ba0123a4" width="30%">

#### **Explanation:**

The nodes **10 and 5** were swapped by mistake. After swapping them back, the BST is restored correctly.

### **Constraints:**

- $\(1 \leq \text{Number of Nodes} \leq 10^3\)$

## 🎯 **My Approach:**

### **Optimized Inorder Traversal (`O(N)` Time, `O(H)` Space)**

1. **Use an inorder traversal** to detect swapped nodes in the BST.
2. **Identify the two misplaced nodes:**
   - If a node appears **larger than the next node**, it's incorrectly placed.
   - Track the **first misplaced node** and the **second misplaced node**.
3. **Swap the values of the two misplaced nodes** to restore the BST.

### **Algorithm Steps:**

1. **Perform an inorder traversal** to find the two misplaced nodes.
2. If the first misplaced node is found, store it in `first`.
3. If a second misplaced node is found later, store it in `last`.
4. If there's no second misplaced node, use the `middle` node instead.
5. **Swap the values** of the two misplaced nodes.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, since we traverse each node once.
- **Expected Auxiliary Space Complexity:** `O(H)`, due to the recursion stack in the inorder traversal.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    Node first, middle, last, prev;

    void inorder(Node root) {
        if (root == null) return;
        inorder(root.left);
        if (prev != null && root.data < prev.data) {
            if (first == null) {
                first = prev;
                middle = root;
            } else {
                last = root;
            }
        }
        prev = root;
        inorder(root.right);
    }

    void correctBST(Node root) {
        first = middle = last = prev = null;
        inorder(root);
        int temp = first.data;
        first.data = (last != null) ? last.data : middle.data;
        if (last != null) last.data = temp;
        else middle.data = temp;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
