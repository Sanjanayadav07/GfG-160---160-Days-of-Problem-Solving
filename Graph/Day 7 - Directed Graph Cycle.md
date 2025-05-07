---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
---

#  _Day 7. Directed Graph Cycle_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/detect-cycle-in-a-directed-graph)

> Note: Sorry for uploading late, my Final Sem exam is going on.

## 💡 **Problem Description:**

Given a **Directed Graph** with **V** vertices (numbered from 0 to V-1) and **E** edges, determine whether the graph contains any cycle.  
The graph is represented as a 2D vector `edges[][]`, where each entry `edges[i] = [u, v]` denotes an edge from vertex **u** to **v**.


## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
```
V = 4, edges[][] = [[0, 1], [1, 2], [2, 3], [3, 3]]
```

<img src="https://github.com/user-attachments/assets/21442886-5a6a-4278-86ae-bc2b7d397a96" width="40%">

#### **Output:**
```
true
```

#### **Explanation:**
There is a self-loop at vertex 3 (3 -> 3) which forms a cycle.


### **Example 2:**

#### **Input:**
```
V = 3, edges[][] = [[0, 1], [1, 2]]
```

<img src="https://github.com/user-attachments/assets/e029ecbb-377d-4dcb-bf42-01eed3f04149" width="40%">

#### **Output:**
```
false
```

#### **Explanation:**
There is no cycle in the graph.


## 🎯 **My Approach:**

### **Kahn’s Algorithm (BFS-based Cycle Detection)**

1. **Build the Graph and Compute In-Degrees:**  
   - Convert the edge list into an adjacency list.
   - Compute the in-degree for each vertex.

2. **Initialize a Queue:**  
   - Add all vertices with zero in-degree into a queue.

3. **Process Vertices:**  
   - While the queue is not empty, remove a vertex and decrement the in-degree of its neighbors.
   - If any neighbor’s in-degree becomes zero, add it to the queue.
   - Count the number of vertices processed.

4. **Cycle Check:**  
   - If the count of processed vertices is not equal to V, a cycle exists.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(V + E), since each vertex and edge is processed once.
- **Expected Auxiliary Space Complexity:** O(V + E), due to the in-degree array, adjacency list, and queue.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public boolean isCyclic(int V, int[][] edges) {
        List<Integer>[] g = new ArrayList[V];
        int[] in = new int[V];
        for (int i = 0; i < V; i++) g[i] = new ArrayList<>();
        for (int[] e : edges) { g[e[0]].add(e[1]); in[e[1]]++; }
        Queue<Integer> q = new ArrayDeque<>();
        for (int i = 0; i < V; i++) if (in[i] == 0) q.add(i);
        int c = 0;
        while (!q.isEmpty()) {
            int u = q.poll(); c++;
            for (int v : g[u]) if (--in[v] == 0) q.add(v);
        }
        return c != V;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
