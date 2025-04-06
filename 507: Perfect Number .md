# 🌟 LeetCode 507: Perfect Number

## 🧠 Problem Statement

> A **perfect number** is a **positive integer** that is equal to the **sum of its positive divisors**, excluding the number itself.
> A **divisor** of an integer `x` is an integer that can divide `x` evenly.

🎯 **Goal**: Given an integer `num`, return `true` if it's a perfect number, otherwise return `false`.

---

## 🧪 Examples

### ✅ Example 1:
```
Input: num = 28
Output: true
Explanation: 28 = 1 + 2 + 4 + 7 + 14
```

### ❌ Example 2:
```
Input: num = 7
Output: false
```

---

## 🧾 Constraints
```
1 <= num <= 10^8
```

---

## ☕ Java Solution

```java
class Solution {
    public boolean checkPerfectNumber(int num) {
        int i = 1, sum = 0;
        while (i <= (num / 2)) {
            if (num % i == 0)
                sum += i;
            i++;
        }
        return sum == num;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def checkPerfectNumber(self, num: int) -> bool:
        if num <= 1:
            return False
        total = 1
        for i in range(2, int(num**0.5)+1):
            if num % i == 0:
                total += i
                if i != num // i:
                    total += num // i
        return total == num
```

---

## 💻 C++ Solution

```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        if (num <= 1) return false;
        int sum = 1;
        for (int i = 2; i * i <= num; ++i) {
            if (num % i == 0) {
                sum += i;
                if (i != num / i)
                    sum += num / i;
            }
        }
        return sum == num;
    }
};
```

---

## 🧮 Complexity Analysis

| Language | Time Complexity | Space Complexity |
|----------|------------------|------------------|
| Java     | O(n/2)           | O(1)             |
| Python   | O(√n)            | O(1)             |
| C++      | O(√n)            | O(1)             |

---

## 📌 Notes

- ⚠️ Avoid checking all numbers up to `n` for divisibility—optimize with √n bounds.
- 🔁 Skip 1 and num itself in the sum to meet the definition.

---

## ✨ Final Thoughts

🎉 Perfect numbers are rare and special. The first few are 6, 28, 496, 8128...

🧙‍♂️ Use this opportunity to refresh your number theory knowledge!

---

🚀 **Happy Coding, and may your logic always be perfect!**
