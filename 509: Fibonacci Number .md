# 🟢 LeetCode 509: Fibonacci Number

## 📌 Problem Statement

The Fibonacci numbers, commonly denoted as `F(n)`, form a sequence where each number is the sum of the two preceding ones. The sequence starts from `0` and `1`.

### Formula:
```
F(0) = 0  
F(1) = 1  
F(n) = F(n - 1) + F(n - 2), for n > 1
```

### 🚩 Task:
Given an integer `n`, compute and return `F(n)`.

---

## 🧩 Examples

### Example 1:
```
Input: n = 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1
```

### Example 2:
```
Input: n = 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2
```

### Example 3:
```
Input: n = 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3
```

---

## 🔒 Constraints:
```
0 <= n <= 30
```

---

## ✅ Java Solution

```java
class Solution {
    public int fib(int n) {
        if(n == 0)
            return 0;
        else if(n == 1 || n == 2)
            return 1;
        else
            return fib(n - 2) + fib(n - 1);
    }
}
```

### 📝 Notes:
- Classic recursive implementation.
- Exponential time complexity: O(2^n)
- Not suitable for large `n` in production use.

---

## ✅ Python Solution

```python
class Solution:
    def fib(self, n: int) -> int:
        if n == 0:
            return 0
        elif n == 1 or n == 2:
            return 1
        else:
            return self.fib(n - 1) + self.fib(n - 2)
```

---

## ✅ C++ Solution

```cpp
class Solution {
public:
    int fib(int n) {
        if (n == 0)
            return 0;
        else if (n == 1 || n == 2)
            return 1;
        else
            return fib(n - 1) + fib(n - 2);
    }
};
```

---

## 💡 Optimization Tips

| Method       | Time Complexity | Space Complexity | Notes                            |
|--------------|-----------------|------------------|----------------------------------|
| Recursion    | O(2^n)          | O(n)             | Easy to implement, inefficient   |
| Memoization  | O(n)            | O(n)             | Caches previous results          |
| Iterative DP | O(n)            | O(1)             | Best performance and memory safe |

---

🚀 **Pro Tip:**  
For interview settings, **clarify** whether the use of memoization or iteration is preferred over recursion.

🧠 **Always consider optimizing recursion for large inputs.**

---

📚 **Happy Coding!**  
Contributions and alternative implementations are welcome.
