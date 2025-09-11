# **Data Structures and Algorithms**

---

### **Sorting Algorithms**

Sorting algorithms organize data in a specific order (ascending/descending). Here's an overview of popular types:

#### **1. Bubble Sort**
   - **Explanation**: Repeatedly swaps adjacent elements if they are in the wrong order.
   - **Complexity**:
     - Best: \( O(n) \) (when the array is already sorted with an optimization check).
     - Average/Worst: \( O(n^2) \).
   - **Use Case**: Simplicity; teaching purposes.

#### **2. Insertion Sort**
   - **Explanation**: Builds the sorted array one element at a time by inserting unsorted elements in their correct positions.
   - **Complexity**:
     - Best: \( O(n) \) (nearly sorted array).
     - Average/Worst: \( O(n^2) \).
   - **Use Case**: Small datasets, nearly sorted data.

#### **3. Selection Sort**
   - **Explanation**: Repeatedly selects the smallest element from the unsorted portion and swaps it with the first unsorted element.
   - **Complexity**: \( O(n^2) \) for all cases.
   - **Use Case**: Simple to implement but inefficient for large datasets.

#### **4. Quick Sort**
   - **Explanation**: Divides the array into two partitions based on a pivot, then sorts each partition recursively.
   - **Complexity**:
     - Best/Average: \( O(n \log n) \).
     - Worst: \( O(n^2) \) (when pivot is poorly chosen).
   - **Use Case**: Preferred for general-purpose sorting due to efficiency.

#### **5. Merge Sort (Split-Merge Approach)**
   - **Explanation**: Divides the array into halves, recursively sorts them, and merges the sorted halves.
   - **Complexity**: \( O(n \log n) \) for all cases.
   - **Use Case**: Sorting linked lists, stable sorting.

#### **6. Radix Sort**
   - **Explanation**: Non-comparative sorting algorithm that processes digits or characters from the least significant to the most significant.
   - **Complexity**:
     - Best/Average/Worst: \( O(nk) \), where \( k \) is the number of digits in the largest number.
   - **Use Case**: Sorting integers or strings efficiently.

---

### **Data Structures**

#### **1. Queue**
   - **Definition**: Follows the FIFO (First-In-First-Out) principle.
   - **Operations**:
     - `enqueue`: Add an element to the end.
     - `dequeue`: Remove an element from the front.
   - **Use Cases**: Task scheduling, breadth-first search.

#### **2. Stack**
   - **Definition**: Follows the LIFO (Last-In-First-Out) principle.
   - **Operations**:
     - `push`: Add an element to the top.
     - `pop`: Remove the top element.
   - **Use Cases**: Undo operations, depth-first search.

#### **3. Linked List**
   - **Definition**: A sequence of nodes where each node contains data and a pointer to the next node.
   - **Types**:
     - Singly Linked List.
     - Doubly Linked List.
     - Circular Linked List.
   - **Use Cases**: Dynamic memory allocation, efficient insertion/deletion.

#### **4. AVL Tree**
   - **Definition**: A self-balancing binary search tree where the height difference of subtrees for any node is at most 1.
   - **Operations**:
     - Rotations (LL, RR, LR, RL) ensure balance.
   - **Use Cases**: Search-heavy applications requiring balanced trees.

#### **5. B-Tree**
   - **Definition**: A balanced search tree where nodes can have multiple keys, optimizing disk read/write operations.
   - **Use Cases**: Databases and file systems.

#### **6. Trie**
   - **Definition**: A tree-like data structure used for efficient storage and retrieval of strings.
   - **Use Cases**:
     - Auto-complete.
     - Dictionary implementations.
     - Prefix-based searching.

---

### **Graph Algorithms**

#### **1. Depth-First Search (DFS)**
   - **Description**: Explores as far as possible along each branch before backtracking.
   - **Use Case**: Detecting cycles, solving puzzles (e.g., mazes).

#### **2. Breadth-First Search (BFS)**
   - **Description**: Explores all neighbors at the current depth before moving to the next level.
   - **Use Case**: Shortest path in unweighted graphs.

#### **3. Dijkstra's Algorithm**
   - **Description**: Finds the shortest path from a source to all vertices in a weighted graph (non-negative weights).
   - **Use Case**: Network routing protocols.

#### **4. Kruskal's Algorithm**
   - **Description**: Finds the Minimum Spanning Tree (MST) by sorting edges by weight and adding them if no cycles are formed.
   - **Use Case**: Network design (e.g., minimizing wiring costs).

---

### **Dynamic Programming**

A technique for solving problems by breaking them down into overlapping subproblems and storing their results.

#### **1. Memoization**
   - **Description**: Top-down approach; stores the results of already solved subproblems.
   ```java
   int fibonacci(int n, int[] memo) {
       if (n <= 1) return n;
       if (memo[n] != 0) return memo[n];
       memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
       return memo[n];
   }
   ```

#### **2. Tabulation**
   - **Description**: Bottom-up approach; builds solutions iteratively using a table.
   ```java
   int fibonacci(int n) {
       int[] dp = new int[n + 1];
       dp[0] = 0; dp[1] = 1;
       for (int i = 2; i <= n; i++) {
           dp[i] = dp[i - 1] + dp[i - 2];
       }
       return dp[n];
   }
   ```

#### **Use Cases**:
- Knapsack problem.
- Longest Common Subsequence (LCS).
- Matrix Chain Multiplication.

---

### **Sliding Window Problems**

A technique to solve problems involving subarrays or substrings.

#### **Examples**:
1. Maximum sum of subarray of size \( k \).
2. Longest substring with at most \( k \) distinct characters.
3. Minimum window substring.

#### **Code Example**:
```java
int maxSumSubarray(int[] arr, int k) {
    int maxSum = 0, windowSum = 0;
    for (int i = 0; i < arr.length; i++) {
        windowSum += arr[i];
        if (i >= k - 1) {
            maxSum = Math.max(maxSum, windowSum);
            windowSum -= arr[i - (k - 1)];
        }
    }
    return maxSum;
}
```

---

### **Bit Manipulation Techniques**

Operations on binary representations for efficiency.

#### **Common Techniques**:
1. **Check if a number is odd/even**:
   ```java
   boolean isOdd = (num & 1) == 1;
   ```

2. **Set/Clear/Toggle a bit**:
   ```java
   // Set bit at position p
   num |= (1 << p);

   // Clear bit at position p
   num &= ~(1 << p);

   // Toggle bit at position p
   num ^= (1 << p);
   ```

3. **Count set bits**:
   ```java
   int countSetBits(int n) {
       int count = 0;
       while (n > 0) {
           count += (n & 1);
           n >>= 1;
       }
       return count;
   }
   ```

#### **Use Cases**:
- Subset generation.
- Optimized mathematical operations.

---

### **Problem-Solving Techniques**

#### **1. Backtracking**
   - **Description**: Tries to build a solution incrementally and backtracks when it finds the solution is not valid.
   - **Use Cases**: N-Queens, Sudoku Solver.

#### **2. Greedy Algorithms**
   - **Description**: Makes the best choice at each step without considering future consequences.
   - **Use Cases**: Huffman encoding, Activity selection problem.

#### **3. Divide and Conquer**
   - **Description**: Divides the problem into subproblems, solves them, and combines results.
   - **Use Cases**: Merge Sort, Quick Sort, Binary Search.
