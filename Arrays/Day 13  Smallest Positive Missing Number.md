---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Searching  
---

# _Day 13. Smallest Positive Missing Number_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/smallest-positive-missing-number-1587115621)

## 💡 **Problem Description:**

You are given an integer array `arr[]`. Your task is to find the smallest positive number missing from the array.

**Note:** Positive number starts from 1. The array can have negative integers too.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [2, -3, 4, 1, 1, 7]`  
**Output:**  
`3`

**Explanation:**  
Smallest positive missing number is 3.

**Input:**  
`arr[] = [5, 3, 2, 5, 1]`  
**Output:**  
`4`

**Explanation:**  
Smallest positive missing number is 4.

**Input:**  
`arr[] = [-8, 0, -1, -4, -3]`  
**Output:**  
`1`

**Explanation:**  
Smallest positive missing number is 1.

### Constraints:
- $`1 <= arr.size() <= 10^5`$
- $`-10^6 <= arr[i] <= 10^6`$

## 🎯 **My Approach:**

1. **In-place Rearrangement**:  
   - The problem can be solved using an in-place rearrangement technique that places elements at their correct indices.
   - The idea is to rearrange the elements such that for any element `arr[i]`, it should be placed at index `arr[i] - 1`.
   - After rearranging the elements, traverse th## Code (Java)

```java
class Solution {
    public int missingNumber(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n; i++) {
            while (arr[i] > 0 && arr[i] <= n && arr[i] != arr[arr[i] - 1]) {
                int temp = arr[i];
                arr[i] = arr[arr[i] - 1];
                arr[temp - 1] = temp;
            }
        }
        for (int i = 0; i < n; i++) {
            if (arr[i] != i + 1) {
                return i + 1;
            }
        }
        return n + 1;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007
). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐


