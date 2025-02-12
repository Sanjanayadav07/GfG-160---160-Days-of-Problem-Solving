---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Arrays
---
# _Day 4. Rotate Array_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/rotate-array-by-n-elements-1587115621)

## 💡 **Problem Description:**

Given an unsorted array `arr[]`. Rotate the array to the left (counter-clockwise direction) by `d` steps, where `d` is a positive integer. Do the mentioned change in the array in place.

**Note:** Consider the array as circular.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [1, 2, 3, 4, 5]`, `d = 2`  
**Output:**  
`[3, 4, 5, 1, 2]`

**Explanation:**  
When rotated by 2 elements, it becomes `[3, 4, 5, 1, 2]`.

**Input:**  
`arr[] = [2, 4, 6, 8, 10, 12, 14, 16, 18, 20]`, `d = 3`  
**Output:**  
`[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]`

**Explanation:**  
When rotated by 3 elements, it becomes `[8, 10, 12, 14, 16, 18, 20, 2, 4, 6]`.

**Input:**  
`arr[] = [7, 3, 9, 1]`, `d = 9`  
**Output:**  
`[3, 9, 1, 7]`

**Explanation:**  
When we rotate 9 times, we'll get `[3, 9, 1, 7]` as the resultant array.

### Constraints:
- `1 <= arr.size(), d <= 10^5`
- `0 <= arr[i] <= 10^5`

## 🎯 **My Approach:**

   - The idea is to rotate the array in three parts by reversing the elements in each part:
     1. Reverse the first `d` elements.
     2. Reverse the remaining elements from index `d` to `n-1`.
     3. Reverse the entire array to get the final rotated array.
   - This way, we achieve the desired result without using extra space.

2. **Steps:**
   - First, we reverse the first `d` elements.
   - Then, reverse the rest of the array (from index `d` to `n-1`).
   - Finally, reverse the entire array.

## 🕒 **Time and Auxiliary Space Complexity**📝

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)
  
## 📝 **Solution Code**


## Code (Java)

```java
class Solution {
    static void rotateArr(int arr[], int d) {
        int n = arr.length;
        d %= n;
        reverse(arr, 0, d - 1);
        reverse(arr, d, n - 1);
        reverse(arr, 0, n - 1);
    }

    static void reverse(int[] arr, int start, int end) {
        while (start < end) {
            int temp = arr[start];
            arr[start] = arr[end];
            arr[end] = temp;
            start++;
            end--;
        }
    }
}
```

# 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
