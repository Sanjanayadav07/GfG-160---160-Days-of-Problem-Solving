---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Arrays

---

# 🚀 _Day 1. Second Largest_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/second-largest3735)

## 💡 **Problem Description:**

Given an array of positive integers `arr[]`, return the second largest element from the array. If the second largest element doesn't exist, return `-1`.

**Note:** The second largest element should not be equal to the largest element.

## 🔍 **Example Walkthrough:**

**Input:**

```
arr[] = [12, 35, 1, 10, 34, 1]
```

**Output:**

```
34
```

**Explanation:**  
The largest element of the array is 35, and the second largest element is 34.

**Input:**

```
arr[] = [10, 5, 10]
```

**Output:**

```
5
```

**Explanation:**  
The largest element of the array is 10, and the second largest element is 5.

**Input:**

```
arr[] = [10, 10, 10]
```

**Output:**

```
-1
```

**Explanation:**  
The largest element of the array is 10, and there is no distinct second largest element.

### Constraints:

- $\(2 \leq \text{arr.size()} \leq 10^5\)$
- $\(1 \leq \text{arr[i]} \leq 10^5\)$

## 🎯 **My Approach:**

1. **Steps:**

   - Initialize two variables, `first` and `second`, to the smallest possible values.
   - Traverse through the array:
     - If the current element is greater than `first`, update `second` to `first`, and then set `first` to the current element.
     - If the current element is less than `first` but greater than `second`, update `second`.
   - If no valid second largest element is found, return `-1`.

2. **Edge Cases:**
   - If all elements are the same, return `-1`.
   - If the array has only two distinct elements, return the smaller of the two if it’s not equal to the largest.

## 🕒 **Time and Auxiliary Space Complexity**📝

- **Expected Time Complexity:** O(n)
- **Expected Auxiliary Space Complexity:** O(1)

## 📝 **Solution Code**


## Code (Java)

```java
class Solution {
    public int getSecondLargest(int[] arr) {
        int first = Integer.MIN_VALUE;
        int second = Integer.MIN_VALUE;

        for (int num : arr) {
            if (num > first) {
                second = first;
                first = num;
            } else if (num > second && num < first) {
                second = num;
            }
        }

        return second == Integer.MIN_VALUE ? -1 : second;
    }
}
```


# 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---


