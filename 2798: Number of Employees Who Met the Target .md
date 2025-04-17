
# 🧑‍💼 LeetCode Problem 2798: Number of Employees Who Met the Target

## 📘 Problem Statement

There are `n` employees in a company, numbered from `0` to `n - 1`. Each employee `i` has worked for `hours[i]` hours in the company.

The company requires each employee to work for at least `target` hours.

You are given a **0-indexed** array of non-negative integers `hours` of length `n` and a non-negative integer `target`.

🔁 Return the number of employees who worked **at least** `target` hours.

---

## 🔍 Examples

### Example 1:

**Input:**  
`hours = [0,1,2,3,4]`, `target = 2`  
**Output:** `3`

**Explanation:**  
Employees at indices 2, 3, and 4 met the target (2, 3, and 4 hours respectively).

---

### Example 2:

**Input:**  
`hours = [5,1,4,2,2]`, `target = 6`  
**Output:** `0`

**Explanation:**  
No employee worked 6 or more hours.

---

## 🔒 Constraints

- `1 <= hours.length <= 50`  
- `0 <= hours[i], target <= 10⁵`

---

## 💻 Java Solution

```java
class Solution {
    public int numberOfEmployeesWhoMetTarget(int[] hours, int target) {
        int count = 0;
        for (int i = 0; i < hours.length ; i++){
            if(hours[i] >= target)
                count++;
        }
        return count;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def numberOfEmployeesWhoMetTarget(self, hours: List[int], target: int) -> int:
        return sum(1 for h in hours if h >= target)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int numberOfEmployeesWhoMetTarget(vector<int>& hours, int target) {
        int count = 0;
        for (int h : hours) {
            if (h >= target) count++;
        }
        return count;
    }
};
```

---

## ⏱️ Time and Space Complexity

- **Time Complexity:** O(n), where `n` is the length of the `hours` array  
- **Space Complexity:** O(1)

---

## 🌟 Summary

This problem is a classic case of array traversal and condition checking.  
✅ Efficient solution with a single pass.  
📦 Can be optimized further only with hardware-level tricks (not needed).
