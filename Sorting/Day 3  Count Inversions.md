---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Divide and Conquer
  - Sorting
---


# _Day 3. Count Inversions_ 
The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/inversion-of-array-1587115620)

## 💡 **Problem Description:**

Given an array of integers `arr[]`. Find the **Inversion Count** in the array.  

Two elements `arr[i]` and `arr[j]` form an inversion if `arr[i] > arr[j]` and `i < j`.  

Inversion Count indicates how far (or close) the array is from being sorted:
- If the array is already sorted, the inversion count is 0.
- If the array is sorted in reverse order, the inversion count is maximum.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [2, 4, 1, 3, 5]`  
**Output:**  
`3`

**Explanation:**  
The sequence `2, 4, 1, 3, 5` has three inversions: (2, 1), (4, 1), (4, 3).


**Input:**  
`arr[] = [2, 3, 4, 5, 6]`  
**Output:**  
`0`

**Explanation:**  
The array is already sorted, so there are no inversions.


**Input:**  
`arr[] = [10, 10, 10]`  
**Output:**  
`0`

**Explanation:**  
All elements of the array are the same, so there are no inversions.


### Constraints:
- $`1 ≤ arr.size() ≤ 10^5`$ 
- $`1 ≤ arr[i] ≤ 10^4`$  

## 🎯 **My Approach:**

1. **Merge Sort-Based Counting**:  
   - The problem can be efficiently solved using a modified **Merge Sort** algorithm.
   - During the merge step, count the number of inversions based on the positions of elements in the two halves.

2. **Steps:**  
   - **Divide:** Recursively divide the array into two halves.  
   - **Merge:** Merge the two halves while counting inversions.  
   - **Count Inversions:** For every pair `(i, j)` where `arr[i] > arr[j]` and `i < j`, increment the count.  

3. **Advantages:**  
   - This approach efficiently counts inversions with a time complexity of **O(n log n)**, compared to the naive **O(n^2)** method.  

## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n log n), as the algorithm performs a logarithmic number of merge steps, with each step taking linear time.  
- **Expected Auxiliary Space Complexity:** O(n), as we use an additional array for temporary storage during the merge process.

## 📝 **Solution Code**

## Code (Java)

```java

class Solution {
    static int countAndMerge(int[] arr, int l, int m, int r) {
        int n1 = m - l + 1, n2 = r - m;
        
        int[] left = new int[n1];
        int[] right = new int[n2];
        
        for(int i = 0; i < n1; i++) 
            left[i] = arr[l + i];
        
        for(int j = 0; j < n2; j++) 
          right[j] = arr[m + 1 + j];
        
        int res = 0;
        int i = 0, j = 0, k = l;
        
        while(i < n1 && j < n2) {
            if(left[i] <= right[j]) 
            arr[k ++] = left[i++];
            
            else {
                arr[k++] = right[j++];
                res += (n1 - i);
            }
        }

        while(i < n1) 
        arr[k++] = left[i++];
        
        while(j < n2)
        arr[k++] = right[j++];
        
        return res;
        
    }
    // Function to count inversions in the array.
    static int countInv(int[] arr, int l, int r) {
        // Your Code Here
        int res = 0;
        if(l < r) {
            int m =(r + l)/2;
            
            res += countInv(arr,l,m);
            res += countInv(arr, m+1,r);
            
            res += countAndMerge(arr, l, m, r);
        }
        return res;
    }
    static int inversionCount(int[] arr) {
        return countInv(arr,0,arr.length - 1);
    }
}
    
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
