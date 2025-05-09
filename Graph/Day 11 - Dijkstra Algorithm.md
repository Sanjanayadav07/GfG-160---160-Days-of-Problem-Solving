---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
---

#  _Day 11. Dijkstra’s Algorithm_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/implementing-dijkstra-set-1-adjacency-matrix)

## 💡 **Problem Description:**

Given an **undirected, weighted graph** with **V** vertices numbered from **0** to **V-1** and **E** edges, represented by a 2D array `edges[][]` (where each `edges[i] = [u, v, w]` represents an edge between nodes **u** and **v** with weight **w**), find the shortest distance from a given source vertex **src** to all other vertices.  
Return an array of integers where the *ith* element denotes the shortest distance from the source vertex **src** to vertex **i**.

> **Note:** The graph is connected and does not contain any negative weight edge.


> **Note:** Sorry for uploading late, my Final Sem exam is going on.


## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**
```
V = 3
edges[][] = [[0, 1, 1], [1, 2, 3], [0, 2, 6]]
src = 2
```

#### **Output:**
```
[4, 3, 0]
```

#### **Explanation:**  

<img src="https://github.com/user-attachments/assets/c49bf243-bd02-4e76-90cf-a69be01c5e60" width="40%">


- For vertex **0**: The shortest path is `2 -> 1 -> 0` with total distance **4**.  
- For vertex **1**: The shortest path is `2 -> 1` with total distance **3**.  
- For vertex **2**: The distance is **0** as it is the source.


### **Example 2:**

#### **Input:**
```
V = 5
edges[][] = [[0, 1, 4], [0, 2, 8], [1, 4, 6], [2, 3, 2], [3, 4, 10]]
src = 0
```

#### **Output:**
```
[0, 4, 8, 10, 10]
```

#### **Explanation:** 

<img src="https://github.com/user-attachments/assets/b91a8560-bedc-4b4c-9637-22de781f3bc7" width="40%">


- For vertex **1**: The shortest path is `0 -> 1` with total distance **4**.  
- For vertex **2**: The shortest path is `0 -> 2` with total distance **8**.  
- For vertex **3**: The shortest path is `0 -> 2 -> 3` with total distance **10**.  
- For vertex **4**: The shortest path is `0 -> 1 -> 4` with total distance **10**.

### **🔐 Constraints**

- $1 \leq V \leq 10^4$  
- $1 ≤ E = edges.size() ≤ 10^5$
- $0 ≤ edges[i][j] ≤ 10^4$  
- $0 \leq src < V$  
- Edge weights are non-negative


## 🎯 **My Approach:**

### **Optimized Dijkstra’s Algorithm (Min-Heap + Adjacency List)**
1. **Build the Graph:** Convert the given edge list into an adjacency list representation.
2. **Initialize Distances:** Set a distance vector `d[]` with high values and update `d[src] = 0`.
3. **Min-Heap (Priority Queue):** Use a min-heap to pick the node with the smallest tentative distance.
4. **Relaxation:** For each neighboring vertex, update its distance if a shorter path is found.

### **Algorithm Steps:**
1. Convert the edges into an adjacency list `g`.
2. Initialize a distance array `d` of size **V** with a large value (e.g., `1e9`), and set `d[src] = 0`.
3. Push `(0, src)` into a min-heap.
4. While the heap is not empty:
   - Pop the top element (with the smallest tentative distance).
   - If the current distance is greater than the recorded distance, continue to the next.
   - Otherwise, for each adjacent vertex, check if the path through the current vertex gives a smaller distance; update and push the new pair in the heap.
5. Return the distance array `d` as the result.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O((V + E) * log V), since each vertex and edge is processed, and insertion/extraction from the heap takes logarithmic time.
- **Expected Auxiliary Space Complexity:** O(V + E), for the adjacency list and the additional storage used by the heap.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public int[] dijkstra(int V, int[][] edges, int src) {
        // Create adjacency list
        List<List<int[]>> adj = new ArrayList<>();
        for (int i = 0; i < V; i++) {
            adj.add(new ArrayList<>());
        }

        for (int[] edge : edges) {
            int u = edge[0];
            int v = edge[1];
            int w = edge[2];
            adj.get(u).add(new int[]{v, w});
            adj.get(v).add(new int[]{u, w}); // remove if directed
        }

        PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[0]));
        int[] dist = new int[V];
        Arrays.fill(dist, Integer.MAX_VALUE);
        dist[src] = 0;

        pq.offer(new int[]{0, src});

        while (!pq.isEmpty()) {
            int[] curr = pq.poll();
            int currDist = curr[0];
            int node = curr[1];

            for (int[] neighbor : adj.get(node)) {
                int nextNode = neighbor[0];
                int weight = neighbor[1];

                if (currDist + weight < dist[nextNode]) {
                    dist[nextNode] = currDist + weight;
                    pq.offer(new int[]{dist[nextNode], nextNode});
                }
            }
        }

        return dist;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐
