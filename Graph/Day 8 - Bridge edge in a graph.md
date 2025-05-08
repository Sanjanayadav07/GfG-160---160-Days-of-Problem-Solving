---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
---

#  _Day 8. Bridge edge in a graph_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/bridge-edge-in-graph)

## 💡 **Problem Description:**

Given an **undirected graph** with **V** vertices and **E** edges, along with a specific edge connecting vertices **c** and **d**, the task is to determine whether this edge is a **bridge**. An edge (c–d) is considered a bridge if removing it increases the number of connected components in the graph, meaning that vertices c and d were part of the same connected component before, but become disconnected after its removal.

> Note: Sorry for uploading late, my Final Sem exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

<img src="https://github.com/user-attachments/assets/1630b101-9fdd-4c26-958e-986c0b274e33" width="40%">


- V = 5, E = 5
- Edges = {{0, 1}, {1, 2}, {2, 3}, {3, 4}, {2, 4}}
- c = 1, d = 2

#### **Output:**
- True

#### **Explanation:**
Removing the edge between nodes 1 and 2 disconnects the graph, indicating that it is a bridge.

### **Example 2:**

#### **Input:**

<img src="https://github.com/user-attachments/assets/09149db6-b08f-4974-9996-b4d0c6115979" width="40%">


- V = 5, E = 5
- Edges = {{0, 1}, {1, 2}, {2, 3}, {3, 4}, {2, 4}}
- c = 2, d = 4

#### **Output:**
- False

#### **Explanation:**
Removing the edge between nodes 2 and 4 does not affect the connectivity of the graph, indicating that it is not a bridge.

<img src="https://github.com/user-attachments/assets/c88756b4-e3ce-4fc1-b9c1-df4c8677abab" width="40%">


## **Constraints:**
- $1 \leq V, E \leq 10^5$
- $0 \leq c, d \leq V-1$

## 🎯 **My Approach:**

### **Algorithm Steps:**

1. **Build the Adjacency List:** Construct the adjacency list from the given list of edges.

2. **Remove the Edge (c, d):** Temporarily remove the edge by not including it in the adjacency list.

3. **DFS Traversal:**
   - Initialize a visited array to keep track of visited nodes.
   - Start DFS traversal from node c.
   - Mark all reachable nodes from c as visited.

4. **Check Reachability of d:**
   - After the DFS traversal, check if node d has been visited.
   - If node d is not visited, it means removing the edge (c, d) disconnects node d from node c, indicating that the edge is a bridge.

5. **Restore the Edge (c, d):** After the check, restore the edge to its original state in the adjacency list.

## **Code (Java)**

```java
class Solution {
    void dfs(List<List<Integer>> g, boolean[] vis, int u) {
        vis[u] = true;
        for (int v : g.get(u)) if (!vis[v]) dfs(g, vis, v);
    }

    public boolean isBridge(int V, int[][] edges, int c, int d) {
        List<List<Integer>> g = new ArrayList<>();
        for (int i = 0; i < V; i++) g.add(new ArrayList<>());
        for (int[] e : edges)
            if (!(e[0] == c && e[1] == d || e[0] == d && e[1] == c)) {
                g.get(e[0]).add(e[1]);
                g.get(e[1]).add(e[0]);
            }
        boolean[] vis = new boolean[V];
        dfs(g, vis, c);
        return !vis[d];
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
