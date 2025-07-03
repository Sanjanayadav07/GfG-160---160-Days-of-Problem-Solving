---
Difficulty: Easy
Source: 160 Days of Problem Solving
Tags:
  - prefix-sum
  - sliding-window
  - Hash
---

#  _Day 3. Largest Subarray of 0s and 1s_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/prefix-sum-gfg-160/problem/largest-subarray-of-0s-and-1s)

## 💡 **Problem Description:**

You are given a binary array `arr[]` consisting of `0s` and `1s`. Your task is to find the length of the largest subarray that contains an equal number of `0s` and `1s`.

## 🔍 **Example Walkthrough:**

**Input:**  
`arr[] = [1, 0, 1, 1, 1, 0, 0]`  
**Output:**  
`6`

**Explanation:** The subarray `[0, 1, 1, 1, 0, 0]` has an equal number of 0s and 1s (three 0s and three 1s).

**Input:**  
`arr[] = [0, 0, 1, 1, 0]`  
**Output:**  
`4`

**Explanation:** Both `[0, 0, 1, 1]` and `[0, 1, 1, 0]` are valid subarrays with an equal number of 0s and 1s.

**Input:**  
`arr[] = [0]`  
**Output:**  
`0`

**Explanation:** No subarray has an equal number of 0s and 1s.

### Constraints:

- $`1 <= arr.size() <= 10^5`$
- `arr[i]` is either `0` or `1`.

## 🎯 **My Approach:**

### HashMap and Prefix Sum Technique

To solve this problem efficiently, we use a hashmap to store the first occurrence of prefix sums. This helps us determine the length of subarrays with equal numbers of 0s and 1s:

1. Treat `0` as `-1` to convert the problem into finding a subarray with sum `0`.
2. Maintain a `prefix sum` while iterating over the array.
3. Use a hashmap to store the first index where each prefix sum occurs.
4. If the same prefix sum is encountered again, the subarray between these two indices has a sum of `0` (indicating equal numbers of `0s` and `1s`).
5. Update the maximum length for each valid subarray.

### Steps:

1. Initialize a hashmap to store prefix sums and their first occurrence index.
2. Replace all `0s` with `-1` in the array.
3. Traverse the array while maintaining a prefix sum:
   - If the prefix sum is `0`, the subarray from the start to the current index is valid.
   - If the prefix sum has been seen before, calculate the length of the subarray and update the maximum length.
   - Otherwise, store the prefix sum with its index.
4. Return the maximum length.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** O(n), where `n` is the size of the array. Each element is processed once, and hashmap operations (insert and lookup) are O(1) on average.
- **Expected Auxiliary Space Complexity:** O(n), as the hashmap stores at most `n` unique prefix sums.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public int maxLen(int[] arr) {
        Map<Integer, Integer> map = new HashMap<>();
        int sum = 0, maxLen = 0;
        for (int i = 0; i < arr.length; i++) {
            sum += (arr[i] == 0) ? -1 : 1;
            if (sum == 0) maxLen = i + 1;
            else if (map.containsKey(sum)) maxLen = Math.max(maxLen, i - map.get(sum));
            else map.put(sum, i);
        }
        return maxLen;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
