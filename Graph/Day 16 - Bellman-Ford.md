---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - Dynamic Programming
---

#  _Day 16. Bellman-Ford_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/distance-from-the-source-bellman-ford-algorithm)  



## 💡 **Problem Description:**

Given a **weighted graph** with `V` vertices (numbered from `0` to `V-1`) and a list of `E` edges, where each edge is represented as a triplet `[u, v, w]` denoting a **directed edge from `u` to `v`** with weight `w`.

Also given a source vertex `src`.  
Your task is to compute the **shortest distance from the source to all other vertices** using the **Bellman-Ford algorithm**.

- If a vertex is unreachable from the source, mark its distance as **1e8**.
- If the graph contains a **negative weight cycle**, return `[-1]`.

> 📝 **Note:** Sorry for uploading late, my Final Sem exam is going on.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```text
V = 5
edges = [[1, 3, 2], [4, 3, -1], [2, 4, 1], [1, 2, 1], [0, 1, 5]]
src = 0
```

<img src="https://github.com/user-attachments/assets/459e6b36-f56c-4168-a4de-d57077575fbf" width="30%">


#### **Output:**

```text
[0, 5, 6, 6, 7]
```

#### **Explanation:**

- 0 → 1: 5  
- 0 → 1 → 2: 6  
- 0 → 1 → 2 → 4 → 3: 6  
- 0 → 1 → 2 → 4: 7



### **Example 2:**

#### **Input:**

```text
V = 4
edges = [[0, 1, 4], [1, 2, -6], [2, 3, 5], [3, 1, -2]]
src = 0
```

<img src="https://github.com/user-attachments/assets/b0b07197-440a-4611-b5ab-3160dc791247" width="30%">

#### **Output:**

```text
[-1]
```

#### **Explanation:**

- The cycle: 1 → 2 → 3 → 1 has a negative weight → **Negative Cycle Detected**


## **Constraints**

- $\( 1 \leq V \leq 100 \)$
- $\( 1 \leq E = \text{edges.size()} \leq V \times (V-1) \)$
- $\( -1000 \leq w \leq 1000 \)$
- $\( 0 \leq \text{src} < V \)$



## 🎯 **My Approach:**

### Standard Bellman-Ford Algorithm

The Bellman-Ford algorithm is designed to find the shortest paths from a **single source** node to all other nodes, even when **negative edge weights** exist.

### **Algorithm Steps:**

1. Initialize a distance array `dist[]` of size `V` with all elements as `1e8`, and set `dist[src] = 0`.
2. Relax all edges `V - 1` times.
3. Check for negative weight cycles by attempting one more relaxation:
   - If any edge still updates, it means a negative cycle exists → return `[-1]`.



## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** $\( O(V \times E) \)$, as we perform edge relaxation `V-1` times over all `E` edges.

- **Expected Auxiliary Space Complexity:** $\( O(V) \)$, to store the distance array of size `V`.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public int[] bellmanFord(int V, int[][] edges, int src) {
        int[] dist = new int[V];
        Arrays.fill(dist, (int)1e8);
        dist[src] = 0;
        for (int i = 0; i < V - 1; i++)
            for (int[] e : edges)
                if (dist[e[0]] < 1e8 && dist[e[0]] + e[2] < dist[e[1]])
                    dist[e[1]] = dist[e[0]] + e[2];
        for (int[] e : edges)
            if (dist[e[0]] < 1e8 && dist[e[0]] + e[2] < dist[e[1]])
                return new int[]{-1};
        return dist;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007/). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
