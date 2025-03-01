---
Difficulty: Hard  
Source: 160 Days of Problem Solving  
Tags:
  - Sorting
  - Mathematical
---

#  _Day 7. Merge Without Extra Space_ 


The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/merge-two-sorted-arrays-1587115620)


## 💡 **Problem Description:**

Given two sorted arrays `a[]` and `b[]` in non-decreasing order, merge them in sorted order **without using any extra space**.  
Modify `a[]` to contain the first `n` smallest elements, and modify `b[]` to contain the remaining `m` elements in sorted order.  


## 🔍 **Example Walkthrough:**

**Input:**  
`a[] = [2, 4, 7, 10], b[] = [2, 3]`  
**Output:**  
`a[] = [2, 2, 3, 4]`  
`b[] = [7, 10]`  

**Explanation:**  
After merging, the sorted order is `[2, 2, 3, 4, 7, 10]`.  
The first `n` elements go into `a[]`, and the remaining elements go into `b[]`.

**Input:**  
`a[] = [1, 5, 9, 10, 15, 20], b[] = [2, 3, 8, 13]`  
**Output:**  
`a[] = [1, 2, 3, 5, 8, 9]`  
`b[] = [10, 13, 15, 20]`  

**Explanation:**  
After merging, the sorted order is `[1, 2, 3, 5, 8, 9, 10, 13, 15, 20]`.  

**Constraints:**  
- `1 <= a.size(), b.size() <= 10^5`  
- `0 <= a[i], b[i] <= 10^7`


## 🎯 **My Approach:**

This problem can be solved using the **Gap Algorithm**, which reduces the need for extra space while efficiently merging two sorted arrays.  

### Steps:  

1. **Calculate Initial Gap:**  
   - Combine the sizes of both arrays, `n + m`, and compute the initial gap as `(n + m) // 2 + (n + m) % 2`.

2. **Iterative Comparison:**  
   - Using the gap, compare elements in both arrays. Swap them if they are out of order.  
   - Reduce the gap in each iteration until it becomes `0`.

3. **Handle Overlapping Cases:**  
   - Handle cases where elements of `a[]` need to be swapped with `b[]`.

4. **Ensure Final Order:**  
   - After processing, the arrays will be modified in-place to reflect the merged sorted order.


## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O((n + m) * log(n + m))  
   - The gap reduces logarithmically with each iteration (`log(n + m)` iterations).  
   - Each iteration performs comparisons and swaps in O(n + m).  
   - Hence, the total complexity is O((n + m) * log(n + m)).  

- **Expected Auxiliary Space Complexity:** O(1)  
   - No extra space is used; modifications are done in-place.


## 📝 **Solution Code**


## Code (Java)

```java
class Solution {
    private int nextGap(int gap) {
        return (gap <= 1) ? 0 : (gap / 2) + (gap % 2);
    }
    public void mergeArrays(int[] a, int[] b) {
        int n = a.length, m = b.length;
        int gap = n + m;

        for (gap = nextGap(gap); gap > 0; gap = nextGap(gap)) {
            int i, j;
            for (i = 0; i + gap < n; i++) {
                if (a[i] > a[i + gap]) {
                    int temp = a[i];
                    a[i] = a[i + gap];
                    a[i + gap] = temp;
                }
            }
            for (j = (gap > n ? gap - n : 0); i < n && j < m; i++, j++) {
                if (a[i] > b[j]) {
                    int temp = a[i];
                    a[i] = b[j];
                    b[j] = temp;
                }
            }
            for (j = 0; j + gap < m; j++) {
                if (b[j] > b[j + gap]) {
                    int temp = b[j];
                    b[j] = b[j + gap];
                    b[j + gap] = temp;
                }
            }
        }
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---

