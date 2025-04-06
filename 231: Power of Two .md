# 🟢 LeetCode 231: Power of Two

## 📌 Problem Statement

Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

An integer `n` is a power of two if there exists an integer `x` such that `n == 2^x`.

---

## 🧩 Examples

### Example 1:
**Input:** `n = 1`  
**Output:** `true`  
**Explanation:** 2^0 = 1

### Example 2:
**Input:** `n = 16`  
**Output:** `true`  
**Explanation:** 2^4 = 16

### Example 3:
**Input:** `n = 3`  
**Output:** `false`  
**Explanation:** 3 is not a power of two

---

## ✅ Java Solution

```java
class Solution {
    public boolean isPowerOfTwo(int n) {
        if(n <= 0)
            return false;
        else if(n == 1)
            return true;
        else if(n % 2 != 0)
            return false;
        return isPowerOfTwo(n / 2);
    }
}
```

**📝 Explanation:**  
- Base check for `n <= 0`: not a power of two.
- If `n == 1`, it’s 2^0 → true.
- If not divisible by 2, it can’t be a power of 2.
- Recursively divide by 2 and repeat the logic.

---

## ✅ Python Solution

```python
class Solution:
    def isPowerOfTwo(self, n: int) -> bool:
        if n <= 0:
            return False
        return (n & (n - 1)) == 0
```

**📝 Explanation:**  
- Bit manipulation trick: Power of 2 numbers have only one bit set.

---

## ✅ C++ Solution

```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        if (n <= 0) return false;
        return (n & (n - 1)) == 0;
    }
};
```

**📝 Explanation:**  
- Same logic using bitwise AND for optimized check.

---

## 🏆 Summary

| Language | Logic Used              | Time Complexity |
|----------|-------------------------|------------------|
| Java     | Recursion, Modulo check | O(log n)         |
| Python   | Bit Manipulation         | O(1)             |
| C++      | Bit Manipulation         | O(1)             |

🧠 **Key Insight:** Powers of two in binary have exactly one `1`. Use bit tricks for optimal solutions.

---

🚀 **Happy Coding!**
📝 **Feel free to contribute enhancements or optimizations!**
