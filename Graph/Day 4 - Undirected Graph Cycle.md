---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - Union-Find
  - DFS
---

#  _Day 4. Undirected Graph Cycle_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/detect-cycle-in-an-undirected-graph)

## 💡 **Problem Description:**

Given an **undirected graph** with `V` vertices and `E` edges, represented as a 2D vector `edges[][]`, where each entry `edges[i] = [u, v]` denotes an edge between vertices `u` and `v`, determine whether the graph contains a **cycle** or not.

> Note: Sorry for uploading late, my exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
V = 4, E = 4
edges = [[0, 1], [0, 2], [1, 2], [2, 3]]
```

<img src="https://github.com/user-attachments/assets/53d6a47c-3dc5-4e1a-9488-c074cdce0199" width="20%">

#### **Output:**

```
True
```

#### **Explanation:**

There exists a cycle: **1 → 2 → 0 → 1**

### **Example 2:**

#### **Input:**

```
V = 4, E = 3
edges = [[0, 1], [1, 2], [2, 3]]
```

<img src="https://github.com/user-attachments/assets/d2fb5707-47cb-45e2-b9fe-06f0ff5602de" width="20%">

#### **Output:**

```
False
```

#### **Explanation:**

No cycle exists in the given graph.

### **Constraints:**

- $1 \leq V \leq 10^5$
- $1 \leq E = \text{edges.size()} \leq 10^5$

## 🎯 **My Approach:**

## **Optimized Approach: Union-Find with Path Compression**

### **Algorithm Steps:**

-Create Adjacency List from the edge list.
-Initialize visited[] array of size V, all false.
-For each unvisited node i:
-Call DFS(i, parent = -1)
-If DFS returns true, cycle exists.
-In DFS:
-Mark node as visited.
-For each neighbor:
-If not visited → recurse with DFS(neighbor, node)
-If visited and not parent → Cycle found.
-If all DFS calls return false → No cycle.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(E * α(V))`, where `α(V)` is the inverse Ackermann function, which grows extremely slowly and is nearly constant.
- **Expected Auxiliary Space Complexity:** `O(V)`, as we store only the parent array.

  ## 📝 **Solution Code**

  ## **Code (Java)**

```java

  class Solution {
    private boolean isCycleDFS(List<List<Integer>>adj, int u, boolean [] visited,int parent) {
        visited[u] = true;
        
        for(int v : adj.get(u)) {
            if(v == parent) continue;
            
            if(visited[v]) return true;
            
            if(isCycleDFS(adj, v, visited,u)) {
                return true;
            }
        }
        return false;
    }
    public boolean isCycle(int V, int[][] edges) {
        // Code here
        List<List<Integer>>adj = new ArrayList<>();
        
        for(int i = 0; i < V;i++) adj.add(new ArrayList<>());
        
        for(int[] edge : edges)  {
            int u = edge[0];
            int v = edge[1];
            
            adj.get(u).add(v);
            adj.get(v).add(u);
            
        }
        boolean [] visited = new boolean[V];
        
        for(int i = 0; i < V;i++) {
            if(!visited[i] && isCycleDFS(adj,i, visited, -1)) {
                return true;
            }
        }
        return false;
    }
}

```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
