<!-- markdownlint-disable MD033 -->
<h1 align="center">✨ LeetCode 507 - Perfect Number ✨</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Difficulty-Easy-brightgreen.svg" alt="difficulty"/>
  <img src="https://img.shields.io/badge/Topic-Math-orange.svg" alt="topic"/>
  <img src="https://img.shields.io/badge/Status-Solved-blue.svg" alt="status"/>
</p>

---

## 🧠 Problem Statement

> A **perfect number** is a **positive integer** that is equal to the **sum of its positive divisors**, excluding the number itself.  
> A **divisor** of an integer `x` is an integer that can divide `x` evenly.

🎯 **Task**: Return `true` if the number is perfect, else return `false`.

---

## 🔍 Examples

✅ **Example 1:**
```txt
Input: num = 28
Output: true
Explanation: 28 = 1 + 2 + 4 + 7 + 14
```

❌ **Example 2:**
```txt
Input: num = 7
Output: false
```

---

## 📊 Constraints
- 1 <= num <= 10⁸

---

## ☕ Java Solution

```java
class Solution {
    public boolean checkPerfectNumber(int num) {
        int i = 1, sum = 0;
        while (i <= (num / 2)) {
            if (num % i == 0)
                sum = sum + i;
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

## 📈 Complexity Analysis

| Language | Time Complexity | Space Complexity |
|----------|------------------|------------------|
| Java     | O(n/2)           | O(1)             |
| Python   | O(√n)            | O(1)             |
| C++      | O(√n)            | O(1)             |

---

## 🧙 Fun Fact
> The first few perfect numbers are **6**, **28**, **496**, **8128**.  
> All known even perfect numbers are related to Mersenne primes!

---

## 💬 Final Thought

> “Perfection is not attainable. But if we chase perfection, we can catch excellence.” – *Vince Lombardi*

---

<p align="center">
  🚀 Happy Coding!
</p>
