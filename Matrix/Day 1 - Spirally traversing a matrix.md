---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Arrays
  - Matrix
---

#  _Day 1. Spirally Traversing a Matrix_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/matrix-gfg-160/problem/spirally-traversing-a-matrix-1587115621)

## 💡 **Problem Description:**

You are given a rectangular matrix `mat[][]` of size `n x m`. Your task is to return an array while traversing the matrix in a spiral form.

## 🔍 **Example Walkthrough:**

**Input:**  
`mat[][] = [[1, 2, 3, 4], [5, 6, 7, 8], [9, 10, 11, 12], [13, 14, 15, 16]]`  
**Output:**  
`[1, 2, 3, 4, 8, 12, 16, 15, 14, 13, 9, 5, 6, 7, 11, 10]`

<img src="https://github.com/user-attachments/assets/2ed3085d-e462-4b42-aecd-109e4ed636f8" width="48%">

**Input:**  
`mat[][] = [[1, 2, 3, 4, 5, 6], [7, 8, 9, 10, 11, 12], [13, 14, 15, 16, 17, 18]]`  
**Output:**  
`[1, 2, 3, 4, 5, 6, 12, 18, 17, 16, 15, 14, 13, 7, 8, 9, 10, 11]`

**Input:**  
`mat[][] = [[32, 44, 27, 23], [54, 28, 50, 62]]`  
**Output:**  
`[32, 44, 27, 23, 62, 50, 28, 54]`

### Constraints:

- `1 <= n, m <= 1000`
- `0 <= mat[i][j] <= 100`

## 🎯 **My Approach:**

1. **Spiral Traversal Algorithm**:  
   The problem can be efficiently solved by following the four main directions in a loop:

   - Traverse the top row from left to right.
   - Traverse the rightmost column from top to bottom.
   - Traverse the bottom row from right to left.
   - Traverse the leftmost column from bottom to top.  
     After traversing one complete cycle (i.e., the outermost layer), shrink the matrix (i.e., update the boundaries) and repeat until all elements are visited.

2. **Steps:**
   - Define boundaries (`top`, `left`, `bottom`, `right`) to represent the four edges of the matrix.
   - Continue the traversal while the top boundary is less than or equal to the bottom boundary and the left boundary is less than or equal to the right boundary.
   - After each traversal step, adjust the respective boundary.
   - Add elements to the result array and continue until all elements are visited.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n \* m), where `n` is the number of rows and `m` is the number of columns in the matrix. We traverse each element exactly once.
- **Expected Auxiliary Space Complexity:** O(1), as we only use a constant amount of additional space (for the boundary variables).

## 📝 **Solution Code**


## Code (Java)

```java
class Solution {
    public ArrayList<Integer> spirallyTraverse(int[][] mat) {
        ArrayList<Integer> result = new ArrayList<>();
        int top = 0, left = 0, bottom = mat.length - 1, right = mat[0].length - 1;

        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; i++) result.add(mat[top][i]);
            top++;
            for (int i = top; i <= bottom; i++) result.add(mat[i][right]);
            right--;
            if (top <= bottom)
                for (int i = right; i >= left; i--) result.add(mat[bottom][i]);
            bottom--;
            if (left <= right)
                for (int i = bottom; i >= top; i--) result.add(mat[i][left]);
            left++;
        }
        return result;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
