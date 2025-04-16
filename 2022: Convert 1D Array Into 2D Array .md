
# 🚀 LeetCode Problem 2022: Convert 1D Array Into 2D Array

## 📘 Problem Statement

You are given a **0-indexed 1-dimensional (1D)** integer array `original`, and two integers, `m` and `n`.  
Your task is to create a **2-dimensional (2D)** array with `m` rows and `n` columns using **all** elements from `original`.

- The elements from indices `0` to `n - 1` (inclusive) of `original` should form the first row of the constructed 2D array,
- The elements from indices `n` to `2 * n - 1` (inclusive) should form the second row, and so on.

Return an `m x n` 2D array constructed according to the above procedure, or an **empty 2D array** if it is impossible.

---

## 🔍 Examples

### Example 1:

**Input:**  
original = [1,2,3,4], m = 2, n = 2  
**Output:** [[1,2],[3,4]]  
**Explanation:**  
First row: [1,2]  
Second row: [3,4]

---

### Example 2:

**Input:**  
original = [1,2,3], m = 1, n = 3  
**Output:** [[1,2,3]]  
**Explanation:**  
Single row with all elements.

---

### Example 3:

**Input:**  
original = [1,2], m = 1, n = 1  
**Output:** []  
**Explanation:**  
It is impossible to fit 2 elements in a 1x1 2D array.

---

## 🔒 Constraints

- `1 <= original.length <= 5 * 10^4`
- `1 <= original[i] <= 10^5`
- `1 <= m, n <= 4 * 10^4`

---

## 💻 Java Solution

```java
class Solution {
    public int[][] construct2DArray(int[] ori, int m, int n) {
        int[][] empty = {};
        int count = -1;
        int[][] ans = new int[m][n];
        if (m * n != ori.length)
            return empty;
        else {
            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    count++;
                    ans[i][j] = ori[count];
                }
            }
        }
        return ans;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def construct2DArray(self, original, m, n):
        if len(original) != m * n:
            return []
        return [original[i * n:(i + 1) * n] for i in range(m)]
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    vector<vector<int>> construct2DArray(vector<int>& original, int m, int n) {
        if (original.size() != m * n) return {};
        vector<vector<int>> result(m, vector<int>(n));
        for (int i = 0; i < m * n; i++) {
            result[i / n][i % n] = original[i];
        }
        return result;
    }
};
```

---

## ⏱️ Time and Space Complexity

- **Time Complexity:** O(m * n)
- **Space Complexity:** O(m * n)

---

## 🌟 Summary

This problem checks your ability to manipulate arrays and understand index mapping between 1D and 2D data structures. The core logic involves validating size compatibility and then mapping the linear index to a 2D format.
