---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Graph
---

#  _Day 18. Minimum Weight Cycle_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/minimum-weight-cycle)


## 💡 **Problem Description:**

Given an **undirected, weighted graph** with **V vertices** numbered from **0 to V-1**, and **E edges**, find the **minimum weight cycle** in the graph.

Each edge is represented by `edges[i] = [u, v, w]` meaning there is an edge between nodes **u and v** with **weight w**.

If **no cycle** exists, return `-1`.

> ⏰ Note: Sorry for uploading late, my Final Sem exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1**

#### **Input:**

```
V = 5
edges = [
    [0, 1, 2], 
    [1, 2, 2], 
    [1, 3, 1], 
    [1, 4, 1], 
    [0, 4, 3], 
    [2, 3, 4]
]
```

<img src="https://github.com/user-attachments/assets/e703fb35-e446-4183-b06b-d9d3c83c8498" width="30%">


#### **Output:**  
```
6
```

#### **Explanation:** 

<img src="https://github.com/user-attachments/assets/786ce890-a51f-4f07-9177-a0ff18059f72" width="30%">

Minimum-weighted cycle is `0 → 1 → 4 → 0` with total weight = `2 + 1 + 3 = 6`.


### **Example 2**

#### **Input:**

```
V = 5
edges = [
    [0, 1, 3],
    [1, 2, 2],
    [0, 4, 1],
    [1, 4, 2],
    [1, 3, 1],
    [3, 4, 2],
    [2, 3, 3]
]
```

<img src="https://github.com/user-attachments/assets/6ed55a03-6c81-41f0-9e95-7887ac2a6bb3" width="30%">

#### **Output:**  
```
5
```

#### **Explanation:**  

<img src="https://github.com/user-attachments/assets/657330bf-88df-4b3d-a8ec-3b2064426821" width="30%">

Minimum-weighted cycle is `1 → 3 → 4 → 1` with total weight = `1 + 2 + 2 = 5`.


### **Constraints**

- $\(1 \leq V \leq 100\)$  
- $\(1 \leq E = \text{edges.length} \leq 10^3\)$  
- $\(1 \leq \text{edges[i][j]} \leq 100\)$


## 🎯 **My Approach:**

### **Dijkstra-Based (Per Node Check)**

### **Algorithm Steps:**

1. **Build an adjacency list** from the edge list.
2. For **every node `i`** from 0 to V-1:
   - Run **Dijkstra's algorithm** from node `i` to compute the **shortest paths** to all other nodes.
   - While processing neighbors, if you find a **back-edge to an already visited node**, and it **doesn’t form a direct parent-child**, it could form a **cycle**.
   - **Update the minimum cycle weight** if a better cycle is found.
3. After checking from all nodes, return the **minimum cycle length** found, or `-1` if no cycle exists.


#### ✅ **Why It Works**

- Each shortest path computed from `i` guarantees minimal distance to `v`, so combining **two shortest paths** and an **extra edge** efficiently checks all **minimal cycles passing through that edge**.
- The parent check ensures we’re not just tracing the same edge forward and backward.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(V × E × log V), since we run Dijkstra's algorithm (O(E log V)) for each vertex.
- **Expected Auxiliary Space Complexity:** O(V + E), to store the adjacency list, distance array, parent tracking, and priority queue per run.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int findMinCycle(int V, int[][] E) {
        List<int[]>[] A = new ArrayList[V];
        for (int i = 0; i < V; i++) A[i] = new ArrayList<>();
        for (int[] e : E) A[e[0]].add(new int[]{e[1], e[2]});
        int r = Integer.MAX_VALUE;
        for (int i = 0; i < V; i++) {
            int[] D = new int[V], P = new int[V];
            Arrays.fill(D, (int)1e9);
            Arrays.fill(P, -1);
            D[i] = 0;
            PriorityQueue<int[]> Q = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
            Q.add(new int[]{0, i});
            while (!Q.isEmpty()) {
                int[] t = Q.poll(); int d = t[0], u = t[1];
                for (int[] a : A[u]) {
                    int v = a[0], w = a[1];
                    if (D[v] > d + w) {
                        D[v] = d + w; P[v] = u; Q.add(new int[]{D[v], v});
                    } else if (P[u] != v && P[v] != u)
                        r = Math.min(r, D[u] + D[v] + w);
                }
            }
        }
        return r == Integer.MAX_VALUE ? -1 : r;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
