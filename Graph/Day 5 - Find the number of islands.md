---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - DFS
---

#  _Day 5. Find the Number of Islands_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/find-the-number-of-islands)

## 💡 **Problem Description:**

Given a grid of size **n × m** consisting of `'W'` (Water) and `'L'` (Land), find the number of islands. An island is formed by connecting adjacent lands in any of the 8 directions (horizontally, vertically, or diagonally) and is surrounded by water or the grid boundary.

## 🔍 **Example Walkthrough:**

#### **Example 1:**

**Input:**

```
grid[][] = [['L', 'L', 'W', 'W', 'W'],
            ['W', 'L', 'W', 'W', 'L'],
            ['L', 'W', 'W', 'L', 'L'],
            ['W', 'W', 'W', 'W', 'W'],
            ['L', 'W', 'L', 'L', 'W']]
```

**Output:**

```
4
```

**Explanation:**  
There are 4 distinct islands in the grid.

<img src="https://github.com/user-attachments/assets/c9f855fc-e60f-445b-845b-c18ce878613b" width="40%">

#### **Example 2:**

**Input:**

```
grid[][] = [['W', 'L', 'L', 'L', 'W', 'W', 'W'],
            ['W', 'W', 'L', 'L', 'W', 'L', 'W']]
```

**Output:**

```
2
```

**Explanation:**  
There are 2 islands in the grid.

<img src="https://github.com/user-attachments/assets/066b82cd-21a1-4403-9b2c-0025cd47bc30" width="40%">

### **Constraints:**

- $\(1 \leq n, m \leq 500\)$
- `grid[i][j]` ∈ {`'L'`, `'W'`}

## 🎯 **My Approach:**

### **DFS (Recursive Flood Fill – 8 Directions)**

We traverse the grid and whenever we find a land cell `'L'`, we start a **DFS flood fill** marking all connected lands.  
Each such initiation counts as **one island**.

### **Algorithm Steps:**

1. Traverse every cell in the grid.
2. If it's land ('L'), call a recursive DFS function to **flood fill all connected lands** in 8 directions.
3. Mark each visited land as `'W'`.
4. Count each DFS initiation as a distinct island.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n × m), as each cell is processed once.
- **Expected Auxiliary Space Complexity:** O(n × m) in the worst-case scenario (e.g., when the grid is completely filled with land) due to the recursion stack or BFS/stack storage.

## 📝 **Solution Code**


## **Code (Java)**

```java
class Solution{
    public int countIslands(char[][] g){
        int n = g.length, m = g[0].length, ans = 0;
        for(int i = 0; i < n; i++)
            for(int j = 0; j < m; j++)
                if(g[i][j]=='L'){ ans++; dfs(g, i, j, n, m); }
        return ans;
    }
    void dfs(char[][] g, int i, int j, int n, int m){
        if(i < 0 || j < 0 || i >= n || j >= m || g[i][j]=='W') return;
        g[i][j] = 'W';
        for(int a = -1; a <= 1; a++)
            for(int b = -1; b <= 1; b++)
                dfs(g, i + a, j + b, n, m);
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

