---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Graph
  - Matrix
  - Queue
---

#  _Day 3. Rotten Oranges_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/graph-gfg-160/problem/rotten-oranges2536)

## 💡 **Problem Description:**

Given a **matrix** `mat[][]` of size **n × m**, where each cell in the matrix can contain:

- **0** → Empty cell
- **1** → Fresh orange
- **2** → Rotten orange

A **rotten orange** at position `(i, j)` can rot adjacent fresh oranges **(up, down, left, right)** in **one unit of time**. The task is to find the **minimum time required** to rot all fresh oranges. If it's **impossible** to rot all oranges, return **-1**.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
mat[][] = [
  [0, 1, 2],
  [0, 1, 2],
  [2, 1, 1]
]
```

#### **Output:**

```
1
```

#### **Explanation:**

Oranges at positions `(0,2)`, `(1,2)`, and `(2,0)` will rot adjacent oranges in **one unit of time**.

### **Example 2:**

#### **Input:**

```
mat[][] = [[2, 2, 0, 1]]
```

#### **Output:**

```
-1
```

#### **Explanation:**

Oranges at `(0,0)` and `(0,1)` **cannot** rot the orange at `(0,3)`, so it's **impossible**.

### **Example 3:**

#### **Input:**

```
mat[][] = [
  [2, 2, 2],
  [0, 2, 0]
]
```

#### **Output:**

```
0
```

#### **Explanation:**

There are **no fresh oranges**, so the answer is **0**.

## **Constraints**

- $1 \leq n, m \leq 500$
- $1 ≤ mat[0].size() ≤ 500$
- `mat[i][j]` ∈ {0, 1, 2}

## 🎯 **My Approach:**

### **Algorithm Steps:**

1. **Multi-source BFS:**
   - Traverse the matrix to push all rotten orange coordinates into a queue.
   - Also, count the number of fresh oranges.
2. **Level-by-Level Processing:**
   - For each time unit, process all the oranges in the queue.
   - For each rotten orange, try to rot its adjacent fresh oranges (up, down, left, right).
   - If at least one orange is rotted during that level, increment the time counter.
3. **Termination:**
   - If after the BFS there are still fresh oranges left, return **-1**.
   - Otherwise, return the total time elapsed.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** $\(O(n \times m)\)$, since each cell (orange) in the mat is processed at most once during the BFS traversal.
- **Expected Auxiliary Space Complexity:** $\(O(n \times m)\)$, as in the worst case, the queue may contain all the cells simultaneously.

  ## **Code (Java)**

```java
class Solution {
    public int orangesRotting(int[][] a) {
        int n = a.length, m = a[0].length, f = 0, t = 0;
        Queue<int[]> q = new LinkedList<>();
        for (int i = 0; i < n; i++)
            for (int j = 0; j < m; j++) {
                if (a[i][j] == 2)
                    q.add(new int[]{i, j});
                else if (a[i][j] == 1)
                    f++;
            }
        if (f == 0) return 0;
        int[][] d = {{1, 0}, {-1, 0}, {0, 1}, {0, -1}};
        while (!q.isEmpty()) {
            int sz = q.size();
            boolean ch = false;
            for (int k = 0; k < sz; k++) {
                int[] p = q.poll();
                int i = p[0], j = p[1];
                for (int[] dir : d) {
                    int x = i + dir[0], y = j + dir[1];
                    if (x < 0 || y < 0 || x >= n || y >= m || a[x][y] != 1)
                        continue;
                    a[x][y] = 2;
                    q.add(new int[]{x, y});
                    f--;
                    ch = true;
                }
            }
            if (ch) t++;
        }
        return f == 0 ? t : -1;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
