# 🧮 LeetCode Problem 172: Factorial Trailing Zeroes

## 📘 Problem Statement

Given an integer `n`, return the number of **trailing zeroes** in `n!` (n factorial).

- Reminder: `n! = n × (n−1) × (n−2) × ... × 1`
- Trailing zeroes are formed by **multiples of 10**, which result from pairs of 2 × 5 in prime factorization.
- Since there are always more 2s than 5s in factorial decompositions, the number of **5s** determines the count of trailing zeroes.

---

## 🔍 Examples

### Example 1:
**Input:** `n = 3`  
**Output:** `0`  
**Explanation:**  
3! = 6 → no trailing zero.

---

### Example 2:
**Input:** `n = 5`  
**Output:** `1`  
**Explanation:**  
5! = 120 → one trailing zero.

---

### Example 3:
**Input:** `n = 0`  
**Output:** `0`  
**Explanation:**  
0! = 1 → no trailing zero.

---

## 🔒 Constraints
- `0 <= n <= 10⁴`

---

## 💻 Java Solution
```java
class Solution {
    public int trailingZeroes(int n) {
        int count = 0;
        while (n > 4) {
            n /= 5;
            count += n;
        }
        return count;
    }
}
```

---

## 🐍 Python Equivalent
```python
class Solution:
    def trailingZeroes(self, n: int) -> int:
        count = 0
        while n >= 5:
            n //= 5
            count += n
        return count
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(log₅n)
- **Space Complexity:** O(1)

---

## 🔍 How It Works
To count the number of times `n!` is divisible by 10:
- We count the **number of 5s** in the prime factors.
- Every multiple of 5 contributes at least one 5.
- Every multiple of 25 contributes one extra 5.
- Every multiple of 125 contributes one more, and so on.

### Example: `n = 100`
- ⌊100 / 5⌋ = 20  
- ⌊100 / 25⌋ = 4  
- ⌊100 / 125⌋ = 0  
→ Total trailing zeroes: **24**

---

## ✅ Evaluation of the Java Solution

### 🔵 Pros:
- ✅ Concise and performant.
- ✅ Correct logic: continuously divides `n` by 5, accumulating the quotient.
- ✅ Complies with problem constraints and runs in logarithmic time.

---

### 🔴 Concerns:
- ⚠️ **Misleading loop condition:**  
  `while(n > 4)` is logically fine but misleading.  
  It breaks if `n = 4`, which should return 0 — and it does — but it's unintuitive.  
  ✅ Better: `while(n >= 5)` (clearer and semantically correct).

---

## ✅ Suggested Fix (Minor Improvement)
```java
class Solution {
    public int trailingZeroes(int n) {
        int count = 0;
        while (n >= 5) {
            n /= 5;
            count += n;
        }
        return count;
    }
}
```

---

## 📌 Final Verdict

| Metric                     | Assessment                      |
|---------------------------|----------------------------------|
| Correctness               | ✅ Accurate for all test cases   |
| Constraint Compliance     | ✅ Fully compliant               |
| Code Clarity              | ⚠️ Could improve readability     |
| Algorithm Choice          | ✅ Optimal (O(log₅n))            |
| Risk of Edge Case Miss    | ❌ No major risk                 |

---

## 🚀 Summary
The trailing zeroes in `n!` depend entirely on the number of 5s in the factorization. This implementation captures that with optimal performance.

> 🔧 Minor refactor suggested for loop condition, but otherwise this is a textbook solution.

