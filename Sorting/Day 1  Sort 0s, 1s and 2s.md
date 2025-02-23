---
Difficulty: Easy  
Source: 160 Days of Problem Solving  
Tags:
  - Sorting
  - Arrays
---

#  _Day 1. Sort 0s, 1s, and 2s_ 


The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/sort-an-array-of-0s-1s-and-2s4231)


## 💡 **Problem Description:**

You are given an array `arr[]` containing only 0s, 1s, and 2s. The task is to sort the array in ascending order. The problem must be solved **in-place**, and the space complexity should be constant.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [0, 1, 2, 0, 1, 2]`  
**Output:**  
`[0, 0, 1, 1, 2, 2]`

**Explanation:**  
The array is sorted into ascending order.

**Input:**  
`arr[] = [0, 1, 1, 0, 1, 2, 1, 2, 0, 0, 0, 1]`  
**Output:**  
`[0, 0, 0, 0, 0, 1, 1, 1, 1, 1, 2, 2]`

**Explanation:**  
The array is sorted into ascending order.

### Constraints:
- `1 <= arr.size() <= 10^6`
- `0 <= arr[i] <= 2`



## 🎯 **My Approach:**

- Initialize three pointers: `low`, `mid`, and `high`.  
   - Use `low` to track the position of `0s`, `high` to track the position of `2s`, and `mid` to traverse the array.  
   - Swap elements as necessary to place `0s`, `1s`, and `2s` in their respective positions.  
   - Continue until `mid` crosses `high`.



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n), as we iterate through the array exactly once, performing constant-time operations during each step.  
- **Expected Auxiliary Space Complexity:** O(1), as we use only three pointers (`low`, `mid`, `high`) and no extra data structures.


## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public void sort012(int[] arr) {
        int low = 0, mid = 0, high = arr.length - 1;

        while (mid <= high) {
            switch (arr[mid]) {
                case 0:
                    int temp0 = arr[low];
                    arr[low] = arr[mid];
                    arr[mid] = temp0;
                    low++;
                    mid++;
                    break;

                case 1:
                    mid++;
                    break;

                case 2:
                    int temp2 = arr[high];
                    arr[high] = arr[mid];
                    arr[mid] = temp2;
                    high--;
                    break;
            }
        }
    }
}
```

## 🎯 **Contribution and Support:**


For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
