---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Searching
  - Matrix
---

#  _Day 5. Search in a sorted Matrix_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/matrix-gfg-160/problem/search-in-a-matrix-1587115621)

## 💡 **Problem Description:**

You are given a strictly sorted 2D matrix `mat[][]` of size `n x m` and a number `x`. Your task is to find whether the number `x` is present in the matrix or not.  
Note: In a strictly sorted matrix, each row is sorted in strictly increasing order, and the first element of the ith row (i!=0) is greater than the last element of the (i-1)th row.

## 🔍 **Example Walkthrough:**

**Input:**  
`mat[][] = [[1, 5, 9], [14, 20, 21], [30, 34, 43]]`, `x = 14`  
**Output:**  
`true`  
**Explanation:**  
14 is present in the matrix, so the output is `true`.

**Input:**  
`mat[][] = [[1, 5, 9, 11], [14, 20, 21, 26], [30, 34, 43, 50]]`, `x = 42`  
**Output:**  
`false`  
**Explanation:**  
42 is not present in the matrix.

**Input:**  
`mat[][] = [[87, 96, 99], [101, 103, 111]]`, `x = 101`  
**Output:**  
`true`  
**Explanation:**  
101 is present in the matrix.

### **Constraints**

- $`1 <= n, m <= 1000`$
- $`1 <= mat[i][j] <= 10^9`$
- $`1 <= x <= 10^9`$

## 🎯 **My Approach:**

### **Binary Search on a Flattened Matrix**

This problem can be solved efficiently using binary search. Even though the matrix is 2D, its structure allows it to be treated as a sorted 1D array where:

- The element at position `(i, j)` in the matrix corresponds to the position `i * m + j` in the flattened array (where `m` is the number of columns).
- Using this, we can perform a binary search directly on the matrix as if it were a 1D array.

### **Steps**:

1. Initialize two pointers, `l = 0` (start) and `r = n * m - 1` (end of the flattened matrix).
2. Use binary search to find the middle index, calculate the corresponding value in the matrix using:
   - `row = mid / m`
   - `col = mid % m`
3. Compare the middle value with `x`:
   - If equal, return `true`.
   - If less than `x`, move the left pointer `l` to `mid + 1`.
   - If greater than `x`, move the right pointer `r` to `mid - 1`.
4. If the loop ends without finding `x`, return `false`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(log(n _ m)), as we perform binary search on a virtual array of size `n _ m`.
- **Expected Auxiliary Space Complexity:** O(1), as we only use a constant amount of additional space.

## 📝 **Solution Code**
## Code (Java)

```java
class Solution {
    public boolean searchMatrix(int[][] mat, int x) {
        int n = mat.length, m = mat[0].length, l = 0, r = n * m - 1;
        while (l <= r) {
            int mid = (l + r) / 2, val = mat[mid / m][mid % m];
            if (val == x) return true;
            if (val < x) l = mid + 1;
            else r = mid - 1;
        }
        return false;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

