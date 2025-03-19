---
Difficulty: Easy  
Source: 160 Days of Problem Solving  
Tags:
  - Arrays
  - Hash
---

#  _Day 2. Count Pair with Given Sum_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/hashing-gfg-160/problem/count-pairs-with-given-sum--150253)

## 💡 **Problem Description:**

Given an array `arr[]` and an integer `target`, find the number of pairs in the array whose sum equals the given target.

## 🔍 **Example Walkthrough:**

Input:  
```
arr[] = [1, 5, 7, -1, 5], target = 6
```
Output:  
```
3
```
Explanation: Pairs with sum `6` are `(1, 5)`, `(7, -1)`, and `(1, 5)`.

Input:  
```
arr[] = [1, 1, 1, 1], target = 2
```
Output:  
```
6
```
Explanation: Pairs with sum `2` are `(1, 1)` repeated `6` times.

Input:  
```
arr[] = [10, 12, 10, 15, -1], target = 125
```
Output:  
```
0
```

### Constraints:
- $\( 1 \leq \text{arr.size()} \leq 10^5 \)$
- $\( -10^4 \leq \text{arr[i]} \leq 10^4 \)$
- $\( 1 \leq \text{target} \leq 10^4 \)$



## 🎯 **My Approach:**

1. **Efficient Hash Map Solution:**
   - Utilize a hash map to store the frequency of each element in the array.
   - For every element in the array, calculate the difference `target - arr[i]` and check if it exists in the hash map. If yes, add the frequency of the difference to the count.
   - Update the hash map to include the current element after processing it, ensuring we count pairs without double-counting.

2. **Optimization:**
   - This approach ensures that we traverse the array only once, keeping time complexity optimal.

3. **Edge Cases:**
   - If the array is empty, return `0`.
   - If no pairs exist with the given sum, return `0`.



## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** \( O(n) \), where \( n \) is the size of the array, as we traverse the array once and perform \( O(1) \) operations for each element.
- **Expected Auxiliary Space Complexity:** \( O(n) \), as we use a hash map to store frequencies of elements.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    int countPairs(int[] arr, int target) {
        HashMap<Integer, Integer> map = new HashMap<>();
        int count = 0;

        for (int num : arr) {
            count += map.getOrDefault(target - num, 0); 
            map.put(num, map.getOrDefault(num, 0) + 1); 
        }

        return count;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, please visit my LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Thank you for your input; together, we strive to create a space where learning is a collaborative endeavor.

⭐ Star this repository if you find it helpful or intriguing! ⭐

---
