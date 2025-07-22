---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 7. Tree Boundary Traversal_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/boundary-traversal-of-binary-tree)

## 💡 **Problem Description:**

Given a binary tree, the task is to return a list of nodes representing its boundary traversal in an **anticlockwise direction**, starting from the **root**. The boundary includes:

1. The **left boundary** (excluding the leaf nodes).
2. All the **leaf nodes** (both from left and right subtrees).
3. The **right boundary** (excluding the leaf nodes), added in **reverse order**.

## 🔍 **Example Walkthrough:**

### **Example 1**

**Input:**  
 `root[] = [1, 2, 3, 4, 5, 6, 7, N, N, 8, 9, N, N, N, N] `

**Output:**  
`[1, 2, 4, 8, 9, 6, 7, 3]`

#### **Explanation:**

<img src="https://github.com/user-attachments/assets/e18cfc62-05ae-4b66-82da-1602ab7cf9af" width="40%">

### **Example 2**

**Input:**  
`root[] = [1, 2, N, 4, 9, 6, 5, N, 3, N, N, N, N 7, 8]`

**Output:**  
`[1, 2, 4, 6, 5, 7, 8]`

#### **Explanation:**

<img src="https://github.com/user-attachments/assets/4318b5b8-868d-4a62-9cdc-92e85e3e4326" width="40%">

### **Example 3**

**Input:**  
`root[] = [1, N, 2, N, 3, N, 4, N, N]`

```
    1
     \
      2
       \
        3
         \
          4
```

**Output:**  
 `[1, 4, 3, 2]`

#### **Explanation:**

- `Left boundary: [1] (as there is no left subtree)`
- `Leaf nodes: [4]`
- `Right boundary: [3, 2] (in reverse order)`
- `Final traversal: [1, 4, 3, 2]`

## **Constraints**

- 1 <= Number of Nodes <= $10^4$
- 1 <= Node Value <= $10^5$

## 🎯 **My Approach:**

The boundary traversal of a binary tree consists of three parts:

1. **Left Boundary:**

   - Traverse the leftmost nodes, **excluding** the leaf nodes.
   - Move **left whenever possible**; otherwise, move **right**.

2. **Leaf Nodes:**

   - Perform **inorder traversal** to collect leaf nodes.

3. **Right Boundary:**
   - Traverse the rightmost nodes, **excluding** the leaf nodes.
   - Move **right whenever possible**; otherwise, move **left**.
   - Store nodes in a stack to reverse them before adding to the final result.

## 🕒 **Time and Auxiliary Space Complexity**

- **Time Complexity:** `O(N)` Each node is visited **at most once**, so the time complexity is **O(N)**.
- **Auxiliary Space Complexity:** `O(H)` (Height of the tree) The recursion stack space in a **skewed tree** can be **O(N)**. In a **balanced tree**, it will be **O(log N)**.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    void lb(Node r, ArrayList<Integer> v) {
        if(r==null || (r.left==null && r.right==null)) return;
        v.add(r.data);
        lb(r.left!=null ? r.left : r.right, v);
    }
    void rb(Node r, ArrayList<Integer> v) {
        if(r==null || (r.left==null && r.right==null)) return;
        rb(r.right!=null ? r.right : r.left, v);
        v.add(r.data);
    }
    void leaf(Node r, ArrayList<Integer> v) {
        if(r==null)return;
        leaf(r.left,v);
        if(r.left==null && r.right==null) v.add(r.data);
        leaf(r.right,v);
    }
    public ArrayList<Integer> boundaryTraversal(Node r) {
        ArrayList<Integer> v = new ArrayList<>();
        if(r==null)return v;
        v.add(r.data);
        lb(r.left, v);
        leaf(r.left, v);
        leaf(r.right, v);
        rb(r.right, v);
        return v;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
