---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
---

#  _Day 6. Topological sort_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/topological-sort)  

## 💡 **Problem Description:**

Given a **Directed Acyclic Graph (DAG)** with V vertices (numbered from 0 to V-1) and E directed edges (represented as a 2D list where each edge is given as `[u, v]` indicating an edge from u to v), return a topological ordering of the vertices.  

A **topological sort** of a DAG is a linear ordering of vertices such that for every directed edge u -> v, vertex u appears before vertex v in the ordering.  
Note: Since there can be multiple valid topological orders, you may return any one of them. The returned ordering is considered correct if for every directed edge u -> v, u comes before v.

## 🔍 **Example Walkthrough:**

### **Example 1:**  

#### **Input:**  
```
V = 4, E = 3  
edges = [[3, 0], [1, 0], [2, 0]]
```

<img src="https://github.com/user-attachments/assets/2a57649a-027b-4ce4-8d29-f5f16724ba29" width="40%">


#### **Output:**  
```
true
```

#### **Explanation:**  
The output `true` denotes that the ordering is valid.  
Few valid topological orders are:  
- [3, 2, 1, 0]  
- [1, 2, 3, 0]  
- [2, 3, 1, 0]  



### **Example 2:**  

#### **Input:**  
```
V = 6, E = 6  
edges = [[1, 3], [2, 3], [4, 1], [4, 0], [5, 0], [5, 2]]
```

<img src="https://github.com/user-attachments/assets/d6e5ea9c-4ffb-4ec5-8ce1-9cdd5b0d6efc" width="40%">


#### **Output:**  
```
true
```

#### **Explanation:**  
The output `true` denotes that the returned ordering is valid.  
Few valid topological orders for this graph are:  
- [4, 5, 0, 1, 2, 3]  
- [5, 2, 4, 0, 1, 3]  



### **Constraints:**  
- 2 ≤ V ≤ 10³  
- 1 ≤ E (edges.size()) ≤ (V * (V - 1)) / 2  



## 🎯 **My Approach:**

### **Kahn’s Algorithm (BFS-based Topological Sort)**

### **Algorithm Steps:**

1. **Construct the Graph:**  
   - Build an **adjacency list** from the edge list.
   - Create an **in-degree array** to store the number of incoming edges for each vertex.

2. **Initialize the Queue:**  
   - Push all vertices with in-degree 0 into a queue.

3. **Process the Queue:**  
   - While the queue is not empty, pop a vertex and add it to the result list.
   - For each neighbor of the popped vertex, reduce its in-degree by 1.
   - If any neighbor's in-degree becomes 0, add it to the queue.

4. **Final Check:**  
   - If the result list contains all vertices, the ordering is valid.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(V + E)`, as every vertex and edge is processed exactly once.
- **Expected Auxiliary Space Complexity:** `O(V + E)`, due to the storage required for the adjacency list, in-degree array, and queue.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public static ArrayList<Integer> topoSort(int V, int[][] edges) {
        ArrayList<ArrayList<Integer>> g = new ArrayList<>();
        int[] in = new int[V];
        ArrayList<Integer> res = new ArrayList<>();
        for (int i = 0; i < V; i++) g.add(new ArrayList<>());
        for (int[] e : edges) {
            g.get(e[0]).add(e[1]);
            in[e[1]]++;
        }
        Queue<Integer> q = new LinkedList<>();
        for (int i = 0; i < V; i++) if (in[i] == 0) q.add(i);
        while (!q.isEmpty()) {
            int u = q.poll();
            res.add(u);
            for (int v : g.get(u)) if (--in[v] == 0) q.add(v);
        }
        return res;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
