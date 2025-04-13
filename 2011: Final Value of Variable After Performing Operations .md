
# 🚀 LeetCode Problem 2011: Final Value of Variable After Performing Operations

## 📘 Problem Statement

There is a programming language with only four operations and one variable `X`:

- `++X` and `X++` increments the value of the variable `X` by 1.
- `--X` and `X--` decrements the value of the variable `X` by 1.

Initially, the value of `X` is 0.

Given an array of strings `operations` containing a list of operations, return the **final value of `X`** after performing all the operations.

---

## 🔍 Examples

### Example 1:

**Input:**  
`operations = ["--X","X++","X++"]`  
**Output:** `1`  
**Explanation:**  
```
Initially, X = 0  
--X -> -1  
X++ -> 0  
X++ -> 1  
```

---

### Example 2:

**Input:**  
`operations = ["++X","++X","X++"]`  
**Output:** `3`  
**Explanation:**  
```
Initially, X = 0  
++X -> 1  
++X -> 2  
X++ -> 3  
```

---

### Example 3:

**Input:**  
`operations = ["X++","++X","--X","X--"]`  
**Output:** `0`  
**Explanation:**  
```
Initially, X = 0  
X++ -> 1  
++X -> 2  
--X -> 1  
X-- -> 0  
```

---

## 🔒 Constraints

- `1 <= operations.length <= 100`
- `operations[i]` is either `"++X"`, `"X++"`, `"--X"`, or `"X--"`.

---

## 💻 Java Solution

```java
class Solution {
    public int finalValueAfterOperations(String[] o) {
        int count = 0;
        for(int i = 0; i < o.length; i++){
            if(o[i].charAt(1) == '+')
                count++;
            else
                count--;
        }
        return count;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def finalValueAfterOperations(self, operations: List[str]) -> int:
        return sum(1 if op[1] == '+' else -1 for op in operations)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int finalValueAfterOperations(vector<string>& operations) {
        int count = 0;
        for (string op : operations) {
            if (op[1] == '+') count++;
            else count--;
        }
        return count;
    }
};
```

---

## ⏱️ Time and Space Complexity

- **Time Complexity:** O(n) where n is the length of operations
- **Space Complexity:** O(1)

---

## 🌟 Summary

This problem tests the understanding of string manipulation and conditional logic. The trick is identifying that the operation type is always determined by the second character (`'+'` or `'-'`).

