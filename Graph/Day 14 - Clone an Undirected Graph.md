---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - BFS
  - DFS
---

# _Day 14. Clone an Undirected Graph_ 


The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/clone-graph)


## 💡 **Problem Description:**

Given a connected undirected graph represented by an adjacency list, `adjList[][]`, with **n** nodes (each node having a distinct label from `0` to `n-1`), your task is to create a **clone** (deep copy) of this graph. Each node in the graph has:  

- An integer `val`
- A list `neighbors` containing references to its adjacent nodes

### **Structure**
```cpp
class Node {
    int val;
    List<Node> neighbors;
}
```

Return a reference to the cloned graph such that the cloned graph is identical to the original graph. The driver code will then print `true` if the clone is correct; otherwise it prints `false`.

> Note: Sorry for uploading late, my Final Sem exam is going on.



## 🔍 **Example Walkthrough:**

### **Example 1**

#### **Input:**

n = 4  
adjList = [[1, 2], [0, 2], [0, 1, 3], [2]]

#### **Output:**
true

#### **Explanation:**  

<img src="https://github.com/user-attachments/assets/eae32789-2302-42bd-83b5-f58a871493ed" width="30%">

The cloned graph is structurally identical to the original. Driver code checks memory and structure integrity.


### **Example 2**

#### **Input:**

n = 3  
adjList = [[1, 2], [0], [0]]

#### **Output:**
true

#### **Explanation:**  

<img src="https://github.com/user-attachments/assets/d248652e-0938-42d1-aad7-8711530cf356" width="30%">

The cloned graph is identical to the original one, hence driver code outputs true.


### **Constraints**

- $\( 1 \leq n \leq 10^4 \)$  
- $\( 0 \leq \text{number of edges} \leq 10^5 \)$  
- $\( 0 \leq \text{adjList[i][j]} < n \)$


## 🎯 **My Approach:**

### **BFS-Based Graph Clone using Queue**

### **Algorithm Steps:**

1. **Initialization:**  
   - If the starting node is `null`, return `null`.
   - Create a hash map (or dictionary) to store mappings from each original node to its clone.
   - Initialize a queue and enqueue the starting node.

2. **BFS Traversal:**  
   - While the queue is not empty:
     - Dequeue the front node.
     - For each neighbor of the dequeued node:
       - If the neighbor hasn't been cloned (i.e., not present in the map), create its clone, store it in the map, and enqueue the neighbor.
       - Append the clone of the neighbor to the `neighbors` list of the clone corresponding to the current node.
       
3. **Return:**  
   - After processing all nodes, return the clone corresponding to the starting node.


## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** `O(N + M)`, where `N` is the number of nodes and `M` is the number of edges. We visit each node and edge exactly once during the clone.
- **Expected Auxiliary Space Complexity:** `O(N)`, used by the hash map and the queue.

## 📝 **Solution Code**


## Code (Java)

```java
class Solution {
    Node cloneGraph(Node node) {
        if (node == null) return null;
        Map<Node, Node> m = new HashMap<>();
        Queue<Node> q = new LinkedList<>();
        m.put(node, new Node(node.val));
        q.add(node);
        while (!q.isEmpty()) {
            for (Node n : q.peek().neighbors) {
                if (!m.containsKey(n)) {
                    m.put(n, new Node(n.val));
                    q.add(n);
                }
                m.get(q.peek()).neighbors.add(m.get(n));
            }
            q.poll();
        }
        return m.get(node);
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
