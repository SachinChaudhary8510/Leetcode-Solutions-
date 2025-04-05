# 🟢 LeetCode 9: Palindrome Number

## 📌 Problem Statement

Given an integer `x`, return `true` if `x` is a **palindrome**, and `false` otherwise.

A **palindrome** is a number that reads the same backward as forward.

---

## 🧩 Examples

### Example 1:
```
Input: x = 121
Output: true
Explanation: 121 reads as 121 from both directions.
```

### Example 2:
```
Input: x = -121
Output: false
Explanation: Reversed it becomes 121-, which is not valid.
```

### Example 3:
```
Input: x = 10
Output: false
Explanation: Reads as 01 from the back, not the same as 10.
```

---

## 🔒 Constraints:
```
-2^31 <= x <= 2^31 - 1
```

---

## ✅ Python Solution

```python
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        c = str(x)
        d = c[::-1]
        if c == d:
            return True
        else:
            return False
```

---

## ✅ Java Solution

```java
class Solution {
    public boolean isPalindrome(int x) {
        String s = Integer.toString(x);
        StringBuilder sb = new StringBuilder(s);
        return s.equals(sb.reverse().toString());
    }
}
```

---

## ✅ C++ Solution

```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        string s = to_string(x);
        string rev = s;
        reverse(rev.begin(), rev.end());
        return s == rev;
    }
};
```

---

## 💡 Optimization Tip

Avoid string conversion to achieve O(1) space complexity. Use integer operations:
- Reverse half of the number and compare.
- Reject negative numbers early.

---

## 🚩 Summary

| Language | Approach          | Complexity           |
|----------|-------------------|----------------------|
| Python   | String reversal   | Time: O(n), Space: O(n) |
| Java     | StringBuilder     | Same as Python       |
| C++      | STL reverse       | Same as Python       |

---

🧠 **Pro Insight:**  
Avoiding string operations is essential in performance-critical applications or interviews that demand space efficiency.

---

📚 **Happy Coding!**  
More optimized approaches? PRs welcome!
