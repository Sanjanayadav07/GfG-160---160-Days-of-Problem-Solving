---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Matrix
---

#  _Day 2. Rotate by 90 degree_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/matrix-gfg-160/problem/rotate-by-90-degree-1587115621)

## 💡 **Problem Description:**

Given a square matrix `mat[][]` of size `n x n`, rotate it by 90 degrees in an anti-clockwise direction without using any extra space.

## 🔍 **Example Walkthrough:**

**Input:**  
`mat[][] = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`  
**Output:**  
`Rotated Matrix: [[3, 6, 9], [2, 5, 8], [1, 4, 7]]`

**Input:**  
`mat[][] = [[1, 2], [3, 4]]`  
**Output:**  
`Rotated Matrix: [[2, 4], [1, 3]]`

### Constraints:

- $`1 ≤ n ≤ 10^2`$
- $`0 ≤ mat[i][j] ≤ 10^3`$

## 🎯 **My Approach:**

1. **In-Place Transposition and Column Reversal:**

   - The matrix can be rotated by performing two operations:
     1. **Transpose the matrix:**  
        Swap `mat[i][j]` and `mat[j][i]` for all `i, j` where `i < j`.
     2. **Reverse each column of the matrix:**  
        For each column, swap elements from the top and bottom.

2. **Steps:**
   - First, transpose the matrix to convert rows into columns.
   - Then, reverse each column to achieve the desired 90-degree rotation in anti-clockwise direction.
   - No extra space is used, and the operations are performed in-place.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n²), where `n` is the size of the matrix. The algorithm involves transposing the matrix (`O(n²)` operations) and then reversing each column (`O(n²)` operations).
- **Expected Auxiliary Space Complexity:** O(1), as all operations are performed in-place, and no additional space is used.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    static void rotateby90(int mat[][]) {
        int n = mat.length;
        for (int i = 0; i < n; i++) {
            for (int j = i; j < n; j++) {
                int temp = mat[i][j];
                mat[i][j] = mat[j][i];
                mat[j][i] = temp;
            }
        }
        for (int j = 0; j < n; j++) {
            for (int i = 0, k = n - 1; i < k; i++, k--) {
                int temp = mat[i][j];
                mat[i][j] = mat[k][j];
                mat[k][j] = temp;
            }
        }
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
