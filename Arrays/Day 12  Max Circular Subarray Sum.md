---
Difficulty: Hard  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays  
---

#  _Day 12. Max Circular Subarray Sum_ 
The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/max-circular-subarray-sum-1587115620)

## 💡 **Problem Description:**

Given an array of integers `arr[]` in a circular fashion, return the maximum sum of a subarray that can be obtained assuming the array is circular.

**Note:** The solution should account for both regular and circular subarrays.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [8, -8, 9, -9, 10, -11, 12]`  
**Output:**  
`22`

**Explanation:**  
Starting from the last element of the array, i.e., `12`, and moving in a circular fashion, the maximum subarray is `[12, 8, -8, 9, -9, 10]`, which gives the maximum sum of `22`.

**Input:**  
`arr[] = [10, -3, -4, 7, 6, 5, -4, -1]`  
**Output:**  
`23`

**Explanation:**  
Maximum sum of the circular subarray is `23`. The subarray is `[7, 6, 5, -4, -1, 10]`.

### Constraints:
- $`1 <= arr.size() <= 10^5`$
- $`-10^4 <= arr[i] <= 10^4`$

## 🎯 **My Approach:**

1. **Kadane's Algorithm for Maximum Subarray Sum:**
   - First, use Kadane’s algorithm to find the maximum subarray sum in the non-circular array (normal subarray sum).
   
2. **Kadane’s Algorithm for Minimum Subarray Sum:**
   - Use Kadane’s algorithm to find the minimum subarray sum in the array. This helps in calculating the circular maximum subarray sum.
   
3. **Total Sum Calculation:**
   - Calculate the total sum of the array and subtract the minimum subarray sum from it. This will give us the maximum circular subarray sum.
   
4. **Final Answer:**
   - The answer is the maximum of:
     - The result from Kadane’s algorithm (non-circular subarray sum).
     - The result from the circular subarray sum calculation (total sum - minimum subarray sum).
   
5. **Handle All Negative Case:**
   - If the entire array consists of negative numbers, return the result from Kadane’s algorithm for the maximum subarray sum.
     
### <div align="center">_*or*_</div>

1. **Kadane’s Algorithm**:
   - The problem is split into two parts: finding the maximum sum of a normal subarray and finding the maximum sum of a circular subarray.
   
2. **Steps:**
   - First, use Kadane's algorithm to find the maximum sum of a regular subarray.
   - Then, calculate the total sum of the array and use Kadane’s algorithm again on the negated values of the array to find the minimum subarray sum.
   - The circular subarray sum is obtained by subtracting the minimum subarray sum from the total sum.
   - Return the maximum of the regular subarray sum and the circular subarray sum.
    
## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n), where `n` is the size of the array. Kadane's algorithm runs in linear time, and we perform only two linear scans of the array.
  
- **Expected Auxiliary Space Complexity:** O(1), as we only use a constant amount of additional space.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public int circularSubarraySum(int[] arr) {
        int totalSum = 0, maxSum = Integer.MIN_VALUE, minSum = Integer.MAX_VALUE;
        int currMax = 0, currMin = 0;
        boolean allNegative = true;

        for (int num : arr) {
            totalSum += num;

            currMax = Math.max(num, currMax + num);
            maxSum = Math.max(maxSum, currMax);

            currMin = Math.min(num, currMin + num);
            minSum = Math.min(minSum, currMin);

            if (num > 0) allNegative = false;
        }

        if (allNegative) return maxSum;

        return Math.max(maxSum, totalSum - minSum);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
