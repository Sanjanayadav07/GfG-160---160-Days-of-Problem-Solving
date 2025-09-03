---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Recursion
  - Backtracking
---

#  _Day 2. Implement Pow_ 

The problem can be found at the following link: [Problem Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/recursion-and-backtracking-gfg-160/problem/powx-n)

## 💡 **Problem Description:**

You are given a floating point number `b` and an integer `e`, and your task is to calculate \( b^e \) (b raised to the power of e).

## 🔍 **Example Walkthrough:**

**Input:**  
`b = 3.00000`, `e = 5`  
**Output:**  
`243.00000`

**Input:**  
`b = 0.55000`, `e = 3`  
**Output:**  
`0.16638`

**Input:**  
`b = -0.67000`, `e = -7`  
**Output:**  
`-16.49971`

### Constraints:

- -100.0 < b < 100.0
- -109 <= e <= $10^9$
- Either b is not zero or e > 0.
- -104 <= be <= $10^4$

## 🎯 **My Approach:**

1. **Optimized Binary Exponentiation:**  
   The problem can be efficiently solved using the binary exponentiation approach (also known as exponentiation by squaring). This method reduces the number of multiplications required to compute \( b^e \) by breaking the problem down recursively.

2. **Steps:**

   - If `e == 0`, return 1, as any number raised to the power of 0 is 1.
   - If `e` is negative, calculate the result using $\( \frac{1}{b^e} \)$.
   - For positive `e`, repeatedly divide `e` by 2, multiplying `b` by itself for each halving of `e`.
   - The result is obtained by squaring the value of `b` for each step and multiplying it with the current result when necessary.

3. **Optimization:**  
   Using a while loop or recursion, the approach reduces the time complexity from O(e) (in the naive approach) to O(log e) , which is significantly faster for large values of `e`.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** $O(log |e|)$, where $(e)$ is the exponent. The exponent is reduced by half in each iteration.
- **Expected Auxiliary Space Complexity:** $O(1)$, as we only use a constant amount of additional space.

## 📝 **Solution Code**

## Code (Java)

```java
class Solution {
    public double power(double b, int e) {
        if (e == 0) return 1.0;
        double half = power(b, e / 2);
        return e % 2 == 0 ? half * half : (e > 0 ? b * half * half : (1.0 / b) * half * half);
    }
}
```

## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
