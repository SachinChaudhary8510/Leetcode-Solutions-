# 🟢 LeetCode 202: Happy Number

## 📌 Problem Statement

Write an algorithm to determine if a number `n` is a **happy number**.

### ✅ Definition

A happy number is defined by the following process:
1. Start with any positive integer.
2. Replace the number with the **sum of the squares of its digits**.
3. Repeat the process until:
   - the number equals **1** (it's a happy number), or
   - it **loops endlessly in a cycle** that does **not** include 1.

Return `true` if `n` is a happy number, and `false` otherwise.

---

## 🧩 Examples

### Example 1:
```
Input: n = 19
Output: true
Explanation:
1^2 + 9^2 = 82
8^2 + 2^2 = 68
6^2 + 8^2 = 100
1^2 + 0^2 + 0^2 = 1
```

### Example 2:
```
Input: n = 2
Output: false
```

---

## 🔒 Constraints:
```
1 <= n <= 2^31 - 1
```

---

## ✅ Java Solution

```java
class Solution {
    public static int sumOfSquare(int num) {
        int sum = 0;
        while (num > 0) {
            int r = num % 10;
            sum += (r * r);
            num /= 10;
        }
        return sum;
    }

    public boolean isHappy(int n) {
        int slow = n, fast = n;

        do {
            slow = sumOfSquare(slow);              // Move one step
            fast = sumOfSquare(sumOfSquare(fast)); // Move two steps
        } while (slow != fast);

        return slow == 1;
    }
}
```

---

## ✅ Python Solution

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        def get_square_sum(num):
            return sum(int(digit)**2 for digit in str(num))

        slow = n
        fast = get_square_sum(n)
        while slow != fast:
            slow = get_square_sum(slow)
            fast = get_square_sum(get_square_sum(fast))
        return slow == 1
```

---

## ✅ C++ Solution

```cpp
class Solution {
public:
    int getSquareSum(int n) {
        int sum = 0;
        while (n > 0) {
            int r = n % 10;
            sum += r * r;
            n /= 10;
        }
        return sum;
    }

    bool isHappy(int n) {
        int slow = n, fast = getSquareSum(n);
        while (slow != fast) {
            slow = getSquareSum(slow);
            fast = getSquareSum(getSquareSum(fast));
        }
        return slow == 1;
    }
};
```

---

## 🚩 Summary

| Language | Technique     | Complexity           |
|----------|---------------|----------------------|
| Java     | Floyd’s Cycle | Time: O(log n), Space: O(1) |
| Python   | Same logic    | Same                 |
| C++      | Same logic    | Same                 |

---

💡 **Pro Tip:** Using Floyd’s Tortoise and Hare algorithm avoids storing visited numbers, keeping space complexity minimal.

---

📚 **Happy Coding!**
