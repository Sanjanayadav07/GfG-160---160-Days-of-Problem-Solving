---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Searching
  - Divide and Conquer
---

#  _Day 7. Allocate Minimum Pages_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/searching-gfg-160/problem/allocate-minimum-number-of-pages0937)


## 💡 **Problem Description:**

You are given an array `arr[]` of integers, where each element `arr[i]` represents the number of pages in the `i`th book. You also have an integer `k` representing the number of students. The task is to allocate books to each student such that:

1. Each student receives **at least one book**.
2. Each student is assigned a **contiguous sequence of books**.
3. No book is assigned to more than one student.

The objective is to minimize the maximum number of pages assigned to any student. In other words, find the arrangement where the student who receives the most pages has the smallest possible maximum.

**Note:** 
- Return `-1` if a valid assignment is not possible.
- Allocation must be **contiguous**.



## 🔍 **Example Walkthrough:**

#### Input:
```
arr[] = [12, 34, 67, 90]
k = 2
```

#### Output:
```
113
```

#### Explanation:
Allocation can be done in the following ways:
1. [12] and [34, 67, 90] → Maximum Pages = 191  
2. [12, 34] and [67, 90] → Maximum Pages = 157  
3. [12, 34, 67] and [90] → Maximum Pages = 113  

The minimum of these cases is `113`, which is selected as the output.



#### Input:
```
arr[] = [15, 17, 20]
k = 5
```

#### Output:
```
-1
```

#### Explanation:
Allocation is not possible as `k > len(arr)`.



#### Input:
```
arr[] = [22, 23, 67]
k = 1
```

#### Output:
```
112
```

#### Constraints:
- $`1 <= arr.size() <= 10^6`$
- $`1 <= arr[i] <= 10^3`$
- $`1 <= k <= 10^3`$



## 🎯 **My Approach:**

1. **Binary Search on Result:**
   - The result lies between `max(arr)` (the maximum pages of a single book) and `sum(arr)` (all pages given to one student).
   - Use binary search to find the smallest valid value.

2. **Validation Function:**
   - Check if it is possible to allocate books such that no student receives more than `mid` pages:
     - Iterate through the books.
     - Add pages to the current student until it exceeds `mid`.
     - If it does, assign to the next student.
   - If the number of students required exceeds `k`, return `False`.

3. **Edge Cases:**
   - If `k > len(arr)`, return `-1` as allocation is not possible.

## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n * log(sum(arr) - max(arr))), where `n` is the size of the array. This is because we perform binary search over the range `[max(arr), sum(arr)]` and validate each mid-point in O(n).
- **Expected Auxiliary Space Complexity:** O(1), as we do not use any additional space apart from a few variables.

## 📝 **Solution Code**
---
Difficulty: Medium  
Source: 160 Days of Problem Solving  
Tags:
  - Searching
  - Divide and Conquer
---

# 🚀 _Day 7. Allocate Minimum Pages_ 🧠

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/searching-gfg-160/problem/allocate-minimum-number-of-pages0937)


## 💡 **Problem Description:**

You are given an array `arr[]` of integers, where each element `arr[i]` represents the number of pages in the `i`th book. You also have an integer `k` representing the number of students. The task is to allocate books to each student such that:

1. Each student receives **at least one book**.
2. Each student is assigned a **contiguous sequence of books**.
3. No book is assigned to more than one student.

The objective is to minimize the maximum number of pages assigned to any student. In other words, find the arrangement where the student who receives the most pages has the smallest possible maximum.

**Note:** 
- Return `-1` if a valid assignment is not possible.
- Allocation must be **contiguous**.



## 🔍 **Example Walkthrough:**

#### Input:
```
arr[] = [12, 34, 67, 90]
k = 2
```

#### Output:
```
113
```

#### Explanation:
Allocation can be done in the following ways:
1. [12] and [34, 67, 90] → Maximum Pages = 191  
2. [12, 34] and [67, 90] → Maximum Pages = 157  
3. [12, 34, 67] and [90] → Maximum Pages = 113  

The minimum of these cases is `113`, which is selected as the output.



#### Input:
```
arr[] = [15, 17, 20]
k = 5
```

#### Output:
```
-1
```

#### Explanation:
Allocation is not possible as `k > len(arr)`.



#### Input:
```
arr[] = [22, 23, 67]
k = 1
```

#### Output:
```
112
```

#### Constraints:
- $`1 <= arr.size() <= 10^6`$
- $`1 <= arr[i] <= 10^3`$
- $`1 <= k <= 10^3`$



## 🎯 **My Approach:**

1. **Binary Search on Result:**
   - The result lies between `max(arr)` (the maximum pages of a single book) and `sum(arr)` (all pages given to one student).
   - Use binary search to find the smallest valid value.

2. **Validation Function:**
   - Check if it is possible to allocate books such that no student receives more than `mid` pages:
     - Iterate through the books.
     - Add pages to the current student until it exceeds `mid`.
     - If it does, assign to the next student.
   - If the number of students required exceeds `k`, return `False`.

3. **Edge Cases:**
   - If `k > len(arr)`, return `-1` as allocation is not possible.

## 🕒 **Time and Auxiliary Space Complexity** 

- **Expected Time Complexity:** O(n * log(sum(arr) - max(arr))), where `n` is the size of the array. This is because we perform binary search over the range `[max(arr), sum(arr)]` and validate each mid-point in O(n).
- **Expected Auxiliary Space Complexity:** O(1), as we do not use any additional space apart from a few variables.

## 📝 **Solution Code**

### Code (Java)

```java
class Solution {
    public static int findPages(int[] arr, int k) {
        int n = arr.length;
        if (k > n) return -1; 

        int low = Arrays.stream(arr).max().getAsInt(); 
        int high = Arrays.stream(arr).sum(); 

        while (low < high) {
            int mid = (low + high) / 2;
            int students = 1, sum = 0;

            for (int pages : arr) {
                if ((sum + pages) > mid) {
                    students++;
                    sum = pages;
                } else {
                    sum += pages;
                }
            }

            if (students > k) low = mid + 1;
            else high = mid;
        }
        return low;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---

