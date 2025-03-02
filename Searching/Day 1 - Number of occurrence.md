---
Difficulty: Easy  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Searching
---

#  _Day 1. Number of Occurrences_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/searching-gfg-160/problem/number-of-occurrence2259)


## 💡 **Problem Description:**

Given a sorted array `arr[]` and a number `target`, determine the number of occurrences of `target` in the array.  

If the number does not exist in the array, return `0`.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [1, 1, 2, 2, 2, 2, 3], target = 2`  
**Output:**  
`4`  

**Explanation:**  
`2` occurs 4 times in the array.

**Input:**  
`arr[] = [1, 1, 2, 2, 2, 2, 3], target = 4`  
**Output:**  
`0`  

**Explanation:**  
`4` is not present in the array.

**Input:**  
`arr[] = [8, 9, 10, 12, 12, 12], target = 12`  
**Output:**  
`3`  

**Explanation:**  
`12` occurs 3 times in the array.

### Constraints:
- $`1 ≤ arr.size() ≤ 10^6`$
- $`1 ≤ arr[i] ≤ 10^6`$
- $`1 ≤ target ≤ 10^6`$



## 🎯 **My Approach:**

 **Steps:**  
   - Perform a binary search to find the first occurrence of the target.  
   - Perform another binary search to find the last occurrence of the target.  
   - Subtract the indices of these two boundaries and add `1` to calculate the count.  
   - If the target is not present, return `0`.



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(log n), as binary search operates in logarithmic time.  
- **Expected Auxiliary Space Complexity:** O(1), as only a constant amount of additional space is used.  

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public int countFreq(int[] arr, int target) {
        int low = 0, high = arr.length - 1;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (arr[mid] < target)
                low = mid + 1;
            else
                high = mid;
        }

        if (low >= arr.length || arr[low] != target)
            return 0;

        int first = low;
        high = arr.length - 1;
        while (low < high) {
            int mid = low + (high - low + 1) / 2;
            if (arr[mid] > target)
                high = mid - 1;
            else
                low = mid;
        }

        int last = high;
        return last - first + 1;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
