---
Difficulty: Medium
Source: 160 Days of Problem Solving
Tags:
  - Heap
  - Linked List
---

#  _Day 3. Merge K sorted linked lists_ 

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/batch/gfg-160-problems/track/heap-gfg-160/problem/merge-k-sorted-linked-lists)

## 💡 **Problem Description:**

Given an array **arr[]** of **n sorted linked lists** of different sizes, merge them into a **single sorted linked list** and return the head of the merged list.

## 🔍 **Example Walkthrough:**

### **Example 1:**

#### **Input:**

```plaintext
arr[] = [1 -> 2 -> 3, 4 -> 5, 5 -> 6, 7 -> 8]
```

#### **Output:**

```plaintext
1 -> 2 -> 3 -> 4 -> 5 -> 5 -> 6 -> 7 -> 8
```

#### **Explanation:**

The `arr[]` has **4 sorted linked lists** of sizes **3, 2, 2, 2**.  
1st list: `1 -> 2 -> 3`  
2nd list: `4 -> 5`  
3rd list: `5 -> 6`  
4th list: `7 -> 8`  
After merging, the final sorted linked list is:  
**`1 -> 2 -> 3 -> 4 -> 5 -> 5 -> 6 -> 7 -> 8`**

<img src="https://github.com/user-attachments/assets/f0b570f5-1544-41d6-a8b7-a161381ef9f6" width="40%">

### **Example 2:**

#### **Input:**

```plaintext
arr[] = [1 -> 3, 8, 4 -> 5 -> 6]
```

#### **Output:**

```plaintext
1 -> 3 -> 4 -> 5 -> 6 -> 8
```

#### **Explanation:**

The `arr[]` has **3 sorted linked lists** of sizes **2, 1, 3**.  
1st list: `1 -> 3`  
2nd list: `8`  
3rd list: `4 -> 5 -> 6`  
After merging, the final sorted linked list is:  
**`1 -> 3 -> 4 -> 5 -> 6 -> 8`**

<img src="https://github.com/user-attachments/assets/93a5a368-3a86-4b0a-8534-5ecba01596c4" width="40%">

### **Constraints:**

- $\(1 \leq \text{Total number of nodes} \leq 10^5\)$
- $\(1 \leq \text{node->data} \leq 10^3\)$

## 🎯 **My Approach:**

### **Min-Heap (Priority Queue)**

1. **Use a Min-Heap (Priority Queue)** to store the head of each linked list.
2. Extract the **smallest element** from the heap and add it to the merged list.
3. Move the pointer of the extracted node’s list to the next node and **push it back** into the heap.
4. Repeat until all lists are merged.

### **Algorithm Steps:**

1. **Push the first node of each linked list** into the min-heap.
2. **While the heap is not empty**:
   - Extract the **smallest node** from the heap.
   - Add it to the result linked list.
   - If the extracted node has a next node, push it into the heap.
3. **Return the merged list** starting from the dummy node’s next pointer.

## 🕒 **Time and Auxiliary Space Complexity**

- **Expected Time Complexity:** **O(N log K)**, **Each node is pushed & popped from the heap once** → **O(N log K)** (heap operations).
- **Expected Auxiliary Space Complexity:** **O(K)**, **Heap stores at most K elements at a time** → **O(K) extra space**.

## 📝 **Solution Code**

## **Code (Java)**

```java
class Solution {
    public Node mergeKLists(List<Node> lists) {
        PriorityQueue<Node> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a.data));
        for (Node head : lists) if (head != null) pq.add(head);
        Node dummy = new Node(0), tail = dummy;
        while (!pq.isEmpty()) {
            tail.next = pq.poll();
            tail = tail.next;
            if (tail.next != null) pq.add(tail.next);
        }
        return dummy.next;
    }
}
```
## 🎯 **Contribution and Support:**

For discussions, questions, or doubts related to this solution, feel free to connect on LinkedIn: [Any Questions](https://www.linkedin.com/in/sanjana-yadav007). Let’s make this learning journey more collaborative!

⭐ **If you find this helpful, please give this repository a star!** ⭐

---
