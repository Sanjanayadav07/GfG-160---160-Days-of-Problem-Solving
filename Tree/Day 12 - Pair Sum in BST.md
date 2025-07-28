---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Tree
  - Binary Search Tree
---

#  _Day 12. Pair Sum in BST_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/find-a-pair-with-given-target-in-bst)

## 💡 **Problem Description:**

Given a **Binary Search Tree (BST)** and a target value, check whether there exists a **pair of nodes** in the BST whose sum equals the given target.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
        7
       / \
      3   8
     / \    \
    2   4    9
```

Target = `12`

<img src="https://github.com/user-attachments/assets/aacf824a-2b30-4bba-bf21-dffb9e684328" width="30%">

#### **Output:**

```
True
```

#### **Explanation:**

In the given BST, there exist two nodes **(8 and 4)** that sum up to 12.

### **Example 2:**

#### **Input:**

```
        9
       / \
      5   10
     / \     \
    2   6     12
```

Target = `23`

<img src="https://github.com/user-attachments/assets/085824bb-b0da-46fe-9288-1bc5430e9e5a" width="30%">

#### **Output:**

```
False
```

#### **Explanation:**

No pair of nodes in the BST sum up to 23.

### **Constraints:**

- $\(1 \leq \text{Number of Nodes} \leq 10^5\)$
- $\(1 \leq \text{target} \leq 10^6\)$

## 🎯 **My Approach:**

### **Optimized Two-Pointer on Inorder Traversal (`O(N)` Time, `O(N)` Space)**

1. **Convert BST to sorted array** using inorder traversal.
2. **Use two-pointer approach** (left and right) to find the target sum efficiently.

### **Algorithm Steps:**

1. **Perform an inorder traversal** and store the BST elements in a sorted list.
2. Use **two pointers** (`left` at the start, `right` at the end) and check the sum:
   - If `arr[left] + arr[right] == target`, return `true`.
   - If `arr[left] + arr[right] < target`, move `left++`.
   - If `arr[left] + arr[right] > target`, move `right--`.
3. If no such pair exists, return `false`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N)`, since we traverse each node once.
- **Expected Auxiliary Space Complexity:** `O(N)`, due to storing the inorder traversal.

## 📝 **Solution Code**
## Code (Java)

```java
class Solution {
    public boolean findTarget(Node root, int target) {
        List<Integer> inorder = new ArrayList<>();
        inorderTraversal(root, inorder);
        int left = 0, right = inorder.size() - 1;
        while (left < right) {
            int sum = inorder.get(left) + inorder.get(right);
            if (sum == target) return true;
            if (sum < target) left++;
            else right--;
        }
        return false;
    }

    private void inorderTraversal(Node node, List<Integer> inorder) {
        if (node == null) return;
        inorderTraversal(node.left, inorder);
        inorder.add(node.data);
        inorderTraversal(node.right, inorder);
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
