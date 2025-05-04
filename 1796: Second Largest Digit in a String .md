# 🔢 LeetCode Problem 1796: Second Largest Digit in a String

## 📘 Problem Statement

Given an **alphanumeric string** `s`, return the **second largest numerical digit** that appears in `s`, or `-1` if it does not exist.

> An **alphanumeric string** contains only lowercase English letters and digits.

---

## 🧪 Examples

### Example 1:
**Input:**  
`s = "dfa12321afd"`  
**Output:** `2`  
**Explanation:**  
Digits: `[1, 2, 3]` → Second largest = `2`

---

### Example 2:
**Input:**  
`s = "abc1111"`  
**Output:** `-1`  
**Explanation:**  
Only one digit exists → No second largest → Return `-1`

---

## 📚 Constraints

- `1 <= s.length <= 500`
- `s` contains only **lowercase English letters** and **digits**.

---

## ✅ Java Solution

```java
class Solution {
    public int secondHighest(String s) {
        int a = -1;
        int b = -1;
        for (int i = 0; i < s.length(); i++) {
            if (s.charAt(i) >= '0' && s.charAt(i) <= '9') {
                int digit = s.charAt(i) - '0';
                if (digit > a) {
                    b = a;
                    a = digit;
                } else if (digit > b && digit != a) {
                    b = digit;
                }
            }
        }
        return b;
    }
}
```

- **Time Complexity:** O(n)
- **Space Complexity:** O(1)
- Operates using two trackers (`a` for max, `b` for second max)

---

## 🐍 Python Solution

```python
class Solution:
    def secondHighest(self, s: str) -> int:
        digits = set()
        for c in s:
            if c.isdigit():
                digits.add(int(c))
        sorted_digits = sorted(digits, reverse=True)
        return sorted_digits[1] if len(sorted_digits) > 1 else -1
```

- Uses a set to remove duplicates and sorts the digits.

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int secondHighest(string s) {
        set<int> digits;
        for (char c : s) {
            if (isdigit(c)) {
                digits.insert(c - '0');
            }
        }
        if (digits.size() < 2) return -1;

        auto it = digits.rbegin(); // Largest
        ++it;                      // Second largest
        return *it;
    }
};
```

- C++ `set` keeps digits sorted and unique by design.

---

## 🔍 Complexity Analysis

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(n)          |
| Space Complexity | O(1) (Max 10 digits) |

---

## 🧠 Key Insights

- We're only dealing with **0–9** → constant space if handled smartly.
- Use ASCII check or `isdigit()` for fast digit filtering.
- Maintain top two values manually to avoid full sorting.

---

## 🧪 Edge Case Testing

| Input            | Output |
|------------------|--------|
| `"9876543210"`   | `8`    |
| `"1"`            | `-1`   |
| `"a2b3c3d2"`     | `2`    |
| `"abc"`          | `-1`   |

---

## ✅ Final Verdict

| Area             | Verdict         |
|------------------|-----------------|
| Time Efficiency  | ✅ Optimal       |
| Space Usage      | ✅ Constant      |
| Code Structure   | ✅ Clear         |
| Edge Handling    | ✅ Robust        |

> This is a textbook use-case for manual two-variable tracking to avoid unnecessary memory usage or sorting.

