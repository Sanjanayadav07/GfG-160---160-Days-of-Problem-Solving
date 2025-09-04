---
Difficulty: Hard
Source: 160 Days of Problem Solving
Tags:
  - Backtracking
---

#  _Day 3. N-Queen Problem_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/recursion-and-backtracking-gfg-160/problem/n-queen-problem0315)

## 💡 **Problem Description:**

The N-Queen problem is a classic combinatorial problem where you are tasked with placing `N` queens on an `N x N` chessboard such that no two queens threaten each other. This means:

- No two queens share the same row.
- No two queens share the same column.
- No two queens share the same diagonal.

Your task is to return a list of all possible solutions, where each solution represents the board configuration as a list of integers. Each integer in the list represents the column index (1-based) of the queen for each row.

![image](https://github.com/user-attachments/assets/ec8facf8-b951-4455-8a96-4e6dbdab1936)

## 🔍 **Example Walkthrough:**

### Example 1

**Input:**  
`N = 4`

**Output:**  
`[[2, 4, 1, 3], [3, 1, 4, 2]]`

**Explanation:**  
For `N = 4`, two solutions exist:

- Solution 1:
  ```
  . Q . .
  . . . Q
  Q . . .
  . . Q .
  ```
- Solution 2:
  ```
  . . Q .
  Q . . .
  . . . Q
  . Q . .
  ```

### Example 2

**Input:**  
`N = 1`

**Output:**  
`[[1]]`

**Explanation:**  
For `N = 1`, only one solution exists:

- Solution 1:
  ```
  Q
  ```

## **Constraints**

- `1 <= N <= 10`

## 🎯 **My Approach:**

The N-Queen problem can be efficiently solved using **bitwise operations** to track occupied columns and diagonals:

1. Use three bitmasks:
   - `cols`: Tracks occupied columns.
   - `d1`: Tracks occupied left diagonals (sum of row and column indices is constant).
   - `d2`: Tracks occupied right diagonals (difference of row and column indices is constant).
2. Backtrack recursively:
   - Place a queen in a valid column of the current row.
   - Mark the column and diagonals as occupied.
   - Move to the next row.
   - If a solution is found, add it to the result.
   - Backtrack by unmarking the column and diagonals.

This method reduces unnecessary checks and speeds up the solution.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:**
- **O(N!)**, where **N** is the number of queens.  
  Each row has **N** possibilities initially, and this reduces with each row.
- **Worst-Case Time Complexity:** **O(N!)**

  - For the first queen, there are `N` choices.
  - For the second queen, there are `N-1` choices, and so on.
  - Thus, the total complexity is `O(N * (N-1) * (N-2) * ... * 1) = O(N!)`.

- **Expected Auxiliary Space Complexity:** **O(N)**, where **N** is the space used for recursive calls and the row configuration array.

## 📝 **Solution Code**
```java
class Solution {
    public ArrayList<ArrayList<Integer>> nQueen(int n) {
        if (n < 4 && n != 1) return new ArrayList<>();
        ArrayList<ArrayList<Integer>> res = new ArrayList<>();
        int[] row = new int[n];
        solve(0, 0, 0, 0, n, row, res);
        return res;
    }

    private void solve(int c, int cols, int d1, int d2, int n, int[] row, ArrayList<ArrayList<Integer>> res) {
        if (c == n) {
            ArrayList<Integer> temp = new ArrayList<>();
            for (int r : row) temp.add(r + 1);
            res.add(temp);
            return;
        }
        for (int r = 0, pos = 1; r < n; ++r, pos <<= 1)
            if ((cols & pos) == 0 && (d1 & (pos << c)) == 0 && (d2 & (pos << (n - 1 - c))) == 0) {
                row[c] = r;
                solve(c + 1, cols | pos, d1 | (pos << c), d2 | (pos << (n - 1 - c)), n, row, res);
            }
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
