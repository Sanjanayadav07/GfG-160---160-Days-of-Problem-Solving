---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Tree
---

#  _Day 9. K Sum Paths_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/tree-gfg-160/problem/k-sum-paths)

## 💡 **Problem Description:**

Given a binary tree and an integer **k**, determine the number of downward-only paths where the sum of the node values in the path equals **k**.  
A path can start and end at any node within the tree but must always move downward (from parent to child).

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```
       1
      / \
     2   3
```

k = 3

#### **Output:**

```
2
```

#### **Explanation:**

- **Path 1:** 1 → 2 (Sum = 3)
- **Path 2:** 3 (Sum = 3)

### **Example 2:**

#### **Input:** k = 7

```
         8
       /   \
      4     5
     / \     \
    3   2     2
   / \   \
  3  -2   1
```

<img src="https://github.com/user-attachments/assets/47109f3a-0212-4ed5-8693-239a8c6efec8" width="30%">

#### **Output:**

```
3
```

#### **Explanation:**

The following paths sum to k

<img src="https://github.com/user-attachments/assets/9d9c9ba5-174e-4b59-aa90-10df02e3ff33" width="30%">

### Constraints

- 1 ≤ number of nodes ≤ $10^4$
- -100 ≤ node value ≤ 100
- -109 ≤ k ≤ $10^9$

## 🎯 **My Approach:**

### **Prefix Sum DFS Approach**

1. **Traverse the Tree (DFS):**  
   Use depth-first search (DFS) to traverse the binary tree. As we move from the root to each node, maintain a running sum of node values.

2. **Maintain Prefix Sum Frequencies:**  
   Use a hash map (or dictionary) to store the frequency of each prefix sum encountered along the current path.

   - **Key:** The prefix sum value.
   - **Value:** The number of times this prefix sum has occurred.

3. **Check for Valid Paths:**  
   For each node visited, compute the current running sum. Then check if `(current sum - k)` exists in the hash map.

   - If it does, it indicates that there is a valid subpath ending at the current node whose sum equals **k**.
   - Increase the count by the frequency of `(current sum - k)`.

4. **Recurse and Backtrack:**
   - Recursively process the left and right children with the updated running sum.
   - After processing both subtrees, decrement the frequency of the current prefix sum in the hash map to backtrack (ensuring that paths in other branches are not affected).

## 🕒 **Time and Auxiliary Space Complexity**

**Expected Time Complexity:** O(N), as each node is visited exactly once.  
**Expected Auxiliary Space Complexity:** O(H + N), where H is the height of the tree (for recursion) and N for the hash map.

## 📝 **Solution Code**
## Code (Java)

```java
class Solution {
    Map<Integer,Integer> m = new HashMap<>();
    int cnt = 0;
    void dfs(Node r, int k, int s) {
        if(r==null)return;
        s += r.data;
        if(m.containsKey(s-k)) cnt += m.get(s-k);
        m.put(s, m.getOrDefault(s,0)+1);
        dfs(r.left, k, s);
        dfs(r.right, k, s);
        m.put(s, m.get(s)-1);
        if(m.get(s)==0)m.remove(s);
    }
    public int sumK(Node r, int k) {
        m.put(0,1);
        dfs(r, k, 0);
        return cnt;
    }
}
```


## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ If you find this helpful, please give this repository a star! ⭐

---
