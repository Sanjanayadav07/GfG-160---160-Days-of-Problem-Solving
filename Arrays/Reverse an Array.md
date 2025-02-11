---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - Arrays
---

#  _Day 3. Reverse an Array_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/arrays-gfg-160/problem/reverse-an-array)


## 💡 **Problem Description:**

You are given an array of integers `arr[]`. Your task is to reverse the given array.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr = [1, 4, 3, 2, 6, 5]`  
**Output:**  
`[5, 6, 2, 3, 4, 1]`

**Explanation:**  
The elements of the array are `1 4 3 2 6 5`. After reversing the array, the first element goes to the last position, the second element goes to the second-last position, and so on. Hence, the answer is `[5, 6, 2, 3, 4, 1]`.

**Input:**  
`arr = [4, 5, 2]`  
**Output:**  
`[2, 5, 4]`

**Explanation:**  
The elements of the array are `4 5 2`. The reversed array will be `[2, 5, 4]`.

**Input:**  
`arr = [1]`  
**Output:**  
`[1]`

**Explanation:**  
The array has only a single element, hence the reversed array is the same as the original.

### Constraints:
- $`1 <= arr.size() <= 10^5`$
- $`0 <= arr[i] <= 10^5`$

## 🎯 **My Approach:**

  - The idea is to maintain two pointers:
  - left and right, such that left points at the beginning of the array and right points to the end of the array.
  - While left pointer is less than the right pointer, swap the elements at these two positions. 
  - After each swap, increment the left pointer and decrement the right pointer to move towards the center of array. 
 - This will swap all the elements in the first half with their corresponding element in the second half.

## 📝 **Solution Code**

 ## Code (Java)

```java

class Solution {
    public void reverseArray(int arr[]) {
        // code here
        int left = 0;
        int right = arr.length - 1;
        
        while(left < right) {
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;
            
            //increment left pointer
            left++;
            
            //decrement right pointer 
            right--;
        }
    
    }
}
```



# 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---


