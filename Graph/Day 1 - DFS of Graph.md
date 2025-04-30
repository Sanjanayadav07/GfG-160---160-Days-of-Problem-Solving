---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - DFS
---

#  _Day 1. DFS of Graph_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/depth-first-traversal-for-a-graph)

## 💡 **Problem Description:**

Given a **connected undirected graph** represented by a **2D adjacency list `adj[][]`**, where `adj[i]` represents the list of vertices connected to vertex `i`.  
Perform a **Depth First Search (DFS) traversal** starting from **vertex 0**, visiting vertices from left to right as per the given adjacency list.

Return a list containing the **DFS traversal** of the graph.

**Note:** Traverse nodes in the same order as given in the adjacency list.

> Note: Sorry for uploading late, my exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
adj = [[2, 3, 1],
       [0],
       [0, 4],
       [0],
       [2]]
```

<img src="https://github.com/user-attachments/assets/5ab8ff7f-c58c-4035-9993-4de191cf627b" width="40%">

#### **Output:**

```
[0, 2, 4, 3, 1]
```

#### **Explanation:**

The DFS traversal proceeds as follows:

- **Start at vertex `0`** → Output: `[0]`
- **Visit `2` (first neighbor of `0`)** → Output: `[0, 2]`
- **Visit `4` (first neighbor of `2`)** → Output: `[0, 2, 4]`
- **Backtrack to `2`, then backtrack to `0`, visit `3`** → Output: `[0, 2, 4, 3]`
- **Backtrack to `0` and visit `1`** → Final Output: `[0, 2, 4, 3, 1]`

### **Example 2:**

#### **Input:**

```
adj = [[1, 2],
       [0, 2],
       [0, 1, 3, 4],
       [2],
       [2]]
```

<img src="https://github.com/user-attachments/assets/ab16fb62-988e-4cf6-be87-6aacb50fe9c5" width="40%">

#### **Output:**

```
[0, 1, 2, 3, 4]
```

#### **Explanation:**

The DFS traversal proceeds as follows:

- **Start at vertex `0`** → Output: `[0]`
- **Visit `1` (first neighbor of `0`)** → Output: `[0, 1]`
- **Visit `2` (first neighbor of `1`)** → Output: `[0, 1, 2]`
- **Visit `3` (first neighbor of `2`)** → Output: `[0, 1, 2, 3]`
- **Backtrack to `2` and visit `4`** → Final Output: `[0, 1, 2, 3, 4]`

## **Constraints:**

- $1 \leq$ `adj.size()` $\leq 10^4$
- $1 \leq$ `adj[i][j]` $\leq 10^4$

## 🎯 **My Approach:**

### **Algorithm Steps:**

-Initialize: Create a visited[] array to keep track of visited nodes.
-Create an empty result list to store DFS traversal order.
-Start DFS from Node 0:
-Call the recursive dfs(node) function starting from node 0.
-In the dfs(node) Function:
-Mark the current node as visited.
-Add the current node to the result list.
-Recursively visit all unvisited adjacent nodes.
-Return the Result List after traversal completes..

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(V + E), since each vertex and edge is visited once.
- **Expected Auxiliary Space Complexity:** O(V), as we store the visited array and recursive function calls.

## 📝 **Solution Code**
## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> dfs(ArrayList<ArrayList<Integer>> adj) {
        ArrayList<Integer> r = new ArrayList<>();
        boolean[] v = new boolean[adj.size()];
        for (int i = 0; i < adj.size(); i++) if (!v[i]) go(i, adj, v, r);
        return r;
    }
    void go(int i, ArrayList<ArrayList<Integer>> a, boolean[] v, ArrayList<Integer> r) {
        v[i] = true;
        r.add(i);
        for (int j : a.get(i)) if (!v[j]) go(j, a, v, r);
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
