---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - BFS
---

#  _Day 2. BFS of Graph_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/bfs-traversal-of-graph)

## 💡 **Problem Description:**

Given a **connected undirected graph** represented by a **2D adjacency list `adj[][]`**, where `adj[i]` represents the list of vertices connected to vertex `i`.  
Perform a **Breadth First Search (BFS) traversal** starting from **vertex 0**, visiting vertices from left to right as per the given adjacency list.

Return a list containing the **BFS traversal** of the graph.

**Note:** Traverse nodes in the same order as given in the adjacency list.

> Note: Sorry for uploading late, my exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
adj = [[1, 2, 3],
       [0],
       [0, 4],
       [0],
       [2]]
```

<img src="https://github.com/user-attachments/assets/5ab8ff7f-c58c-4035-9993-4de191cf627b" width="40%">

#### **Output:**

```
[0, 1, 2, 3, 4]
```

#### **Explanation:**

Starting from vertex **0**:

- Visit **0** → Output: `[0]`
- Visit **2** (first neighbor of 0) → Output: `[0, 2]`
- Visit **3** (next neighbor of 0) → Output: `[0, 2, 3]`
- Visit **1** (next neighbor of 0) → Output: `[0, 2, 3]`
- Visit **4** (neighbor of 2) → Final Output: `[0, 2, 3, 1, 4]`

### **Example 2:**

#### **Input:**

```
adj = [[1, 2],
       [0, 3],
       [0, 3, 4],
       [1, 2],
       [2]]
```

<img src="https://github.com/user-attachments/assets/ab16fb62-988e-4cf6-be87-6aacb50fe9c5" width="40%">

#### **Output:**

```
[0, 1, 2, 3, 4]
```

#### **Explanation:**

Starting from vertex **0**:

- Visit **0** → Output: `[0]`
- Visit **1** (first neighbor of 0) → Output: `[0, 1]`
- Visit **2** (next neighbor of 0) → Output: `[0, 1, 2]`
- Visit **3** (first unvisited neighbor of 2) → Output: `[0, 1, 2, 3]`
- Visit **4** (next neighbor of 2) → Final Output: `[0, 1, 2, 3, 4]`

## **Constraints:**

- $1 \leq$ `adj.size()` $\leq 10^4$
- $1 \leq$ `adj[i][j]` $\leq 10^4$

## 🎯 **My Approach:**

### **Iterative BFS (Using Queue)**

### **Algorithm Steps:**

1. Maintain a **visited array** to track visited nodes.
2. Use a **queue** to process nodes in a FIFO manner.
3. Start BFS traversal from node `0` and enqueue it.
4. Process nodes from the queue and visit their unvisited neighbors in order.
5. Store the **BFS traversal sequence** in a list.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(V + E), since each vertex and edge is visited once.
- **Expected Auxiliary Space Complexity:** O(V), as we store the visited array and queue.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public ArrayList<Integer> bfs(ArrayList<ArrayList<Integer>> adj) {
        ArrayList<Integer> r = new ArrayList<>();
        boolean[] v = new boolean[adj.size()];
        Queue<Integer> q = new LinkedList<>();
        q.add(0);
        v[0] = true;

        while (!q.isEmpty()) {
            int i = q.poll();
            r.add(i);
            for (int j : adj.get(i)) {
                if (!v[j]) {
                    v[j] = true;
                    q.add(j);
                }
            }
        }
        return r;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007) Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
