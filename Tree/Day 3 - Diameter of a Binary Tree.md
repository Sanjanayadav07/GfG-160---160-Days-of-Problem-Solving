---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 3. Diameter of a Binary Tree_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/diameter-of-binary-tree)

## 💡 **Problem Description:**

Given a binary tree, the diameter (or width) is defined as the number of edges on the longest path between two leaf nodes in the tree. This path may or may not pass through the root. Your task is to determine the diameter of the tree.

## 🔍 **Example Walkthrough:**

**Input:**  
`root[] = [1, 2, 3]`

<img src="https://github.com/user-attachments/assets/59d0050e-2436-4134-a460-3ab897ac178e" width="30%">

**Output:**  
`2`  
**Explanation:**  
The longest path has 2 edges: (node 2 -> node 1 -> node 3).

**Input:**  
`root[] = [5, 8, 6, 3, 7, 9]`

<img src="https://github.com/user-attachments/assets/2d8bdef5-2cdb-4c5c-9f84-083f96d60d1e" width="30%">

**Output:**  
`4`  
**Explanation:**  
The longest path has 4 edges: (node 3 -> node 8 -> node 5 -> node 6 -> node 9).

### Constraints

- 1 ≤ number of nodes ≤ $10^5$
- 0 ≤ node->data ≤ $10^5$

## 🎯 **My Approach:**

1. **Single DFS Traversal (Pair Method):**  
   Use a recursive function that returns a pair: the height of the current subtree and the diameter computed so far. For each node, compute:
   - The height as `1 + max(height(left), height(right))`.
   - The diameter as the maximum of:
     - The diameter in the left subtree.
     - The diameter in the right subtree.
     - The sum of the heights of the left and right subtrees (which represents the path passing through the current node).

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(N), as each node is visited exactly once.
- **Expected Auxiliary Space Complexity:** O(H), where H is the height of the tree (due to recursion stack).

## 📝 **Solution Code**
## Code (Java)

```java
class Solution {
    int[] f(Node r) {
        if (r == null) return new int[]{0, 0};
        int[] a = f(r.left), b = f(r.right);
        int h = 1 + Math.max(a[0], b[0]);
        int d = Math.max(Math.max(a[1], b[1]), a[0] + b[0]);
        return new int[]{h, d};
    }

    int diameter(Node root) {
        return f(root)[1];
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
