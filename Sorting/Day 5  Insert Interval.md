---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Sorting
---

#  _Day 5. Insert Intervals_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/sorting-gfg-160/problem/insert-interval-1666733333)

## 💡 **Problem Description:**

Geek has an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and the end of the `i`-th event. The array `intervals` is sorted in ascending order by `starti`.

Geek wants to add a new interval `newInterval = [newStart, newEnd]` such that `intervals` is still sorted in ascending order by `starti` and has no overlapping intervals. Merge overlapping intervals if necessary.


## 🔍 **Example Walkthrough:**

**Input:**  
`intervals = [[1,3], [4,5], [6,7], [8,10]], newInterval = [5,6]`  
**Output:**  
`[[1,3], [4,7], [8,10]]`

**Explanation:**  
The `newInterval` `[5,6]` overlaps with `[4,5]` and `[6,7]`, so they are merged into `[4,7]`.


**Input:**  
`intervals = [[1,2], [3,5], [6,7], [8,10], [12,16]], newInterval = [4,9]`  
**Output:**  
`[[1,2], [3,10], [12,16]]`

**Explanation:**  
The `newInterval` `[4,9]` overlaps with `[3,5], [6,7], [8,10]`, so they are merged into `[3,10]`.


### Constraints:

- $`1 ≤ intervals.size() ≤ 10^5`$  
- $`0 ≤ start[i], end[i] ≤ 10^9`$


## 🎯 **My Approach:**

1. **Iterative Merge:**  
   - Traverse the intervals and add those that come entirely before the `newInterval`.  
   - Merge intervals that overlap with `newInterval`.  
   - Add intervals that come entirely after `newInterval`.  

2. **Steps:**  
   - Traverse through the given intervals:
     - If an interval ends before the `newInterval` starts, add it to the result.  
     - If an interval starts after the `newInterval` ends, add the `newInterval` to the result and process the current interval as the next `newInterval`.  
     - Otherwise, merge overlapping intervals by updating the start and end of the `newInterval`.  
   - Append the last `newInterval` to the result after traversal.

3. **Efficiency:**  
   - The approach involves a single traversal of the array, making it optimal.  
   - Merging intervals is straightforward and uses a constant amount of additional space.


## 🕒 **Time and Auxiliary Space Complexity** 

**Expected Time Complexity:**  
O(n), where `n` is the size of the intervals. Traversal through all intervals ensures linear time complexity.

**Expected Auxiliary Space Complexity:**  
O(n), as we store the resulting intervals in a new list.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    static ArrayList<int[]> insertInterval(int[][] intervals, int[] newInterval) {
        ArrayList<int[]> result = new ArrayList<>();
        int i = 0; int n = intervals.length;
        while (i < intervals.length && intervals[i][1] < newInterval[0]) {
            result.add(intervals[i]);
            i++;
        }
        while (i < intervals.length && intervals[i][0] <= newInterval[1]) {
            newInterval[0] = Math.min(newInterval[0], intervals[i][0]);
            newInterval[1] = Math.max(newInterval[1], intervals[i][1]);
            i++;
        }
        result.add(newInterval);
        while (i < intervals.length) {
            result.add(intervals[i]);
            i++;
        }

        return result;
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐  

---
