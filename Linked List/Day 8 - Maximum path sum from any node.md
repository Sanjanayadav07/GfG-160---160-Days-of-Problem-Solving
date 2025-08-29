---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 8. Maximum path sum from any node_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/maximum-path-sum-from-any-node)

## 💡 **Problem Description:**

Given a binary tree, the task is to find the maximum path sum. The path may start and end at any node in the tree.

## 🔍 **Example Walkthrough:**

**Input:**  
`root[] = [10, 2, 10, 20, 1, N, -25, N, N, N, N, 3, 4]`  
**Output:**  
`42`  
**Explanation:**

<img src="https://github.com/user-attachments/assets/c3753c3d-a5a4-422d-8309-8d18099f5f6b" width="40%">

The maximum path sum is represented using the green colored nodes in the binary tree.

**Input:**  
`root[] = [-17, 11, 4, 20, -2, 10]`  
**Output:**  
`31`  
**Explanation:**

<img src="https://github.com/user-attachments/assets/eab45812-cd7f-4020-9e00-e39bb5481183" width="40%">

The maximum path sum is represented using the green colored nodes in the binary tree.

## Constraints:

- 1 ≤ number of nodes ≤ $10^3$
- -10^4 ≤ node->data ≤ $10^4$

## 🎯 **My Approach:**

1. **DFS Post-Order Traversal:**  
   Use a recursive DFS (post-order) approach to calculate, for each node:
   - **maxSingle:** The maximum path sum including the node and at most one of its subtrees.
   - **Global Maximum:** Update a global result with the sum of the node value and the maximum contributions from both left and right subtrees.
2. **Steps:**
   - Recursively compute the maximum path sum from the left and right children.
   - Discard negative sums by taking `max(0, value)`.
   - Update the global maximum with `left + right + node->data`.
   - Return `node->data + max(left, right)` to allow parent nodes to include the maximum available contribution.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n), as each node is visited exactly once.
- **Expected Auxiliary Space Complexity:** O(h), where `h` is the height of the tree (due to the recursion stack). In the worst-case (skewed tree), this can be O(n).

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    int dfs(Node r, int[] res) {
        if (r == null) return 0;
        int l = Math.max(0, dfs(r.left, res)), rgt = Math.max(0, dfs(r.right, res));
        res[0] = Math.max(res[0], l + rgt + r.data);
        return Math.max(l, rgt) + r.data;
    }
    int findMaxSum(Node root) {
        int[] res = {Integer.MIN_VALUE};
        dfs(root, res);
        return res[0];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
