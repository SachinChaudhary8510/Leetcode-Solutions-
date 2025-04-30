# 🔍 LeetCode Problem 1295: Find Numbers with Even Number of Digits

## 📘 Problem Statement

Given an integer array `nums`, return the count of numbers that contain an **even number of digits**.

---

## 🧪 Examples

### Example 1:
**Input:** `nums = [12, 345, 2, 6, 7896]`  
**Output:** `2`  
**Explanation:** `12` and `7896` have even number of digits.

---

### Example 2:
**Input:** `nums = [555, 901, 482, 1771]`  
**Output:** `1`  
**Explanation:** Only `1771` has an even number of digits.

---

## 🔒 Constraints

- \( 1 \leq \text{nums.length} \leq 500 \)
- \( 1 \leq \text{nums}[i] \leq 10^5 \)

---

## 💻 Java Solution

```java
class Solution {
    public int findNumbers(int[] nums) {
        int count = 0;
        for (int i : nums) {
            int numberOfDigits = 0;
            while (i > 0) {
                numberOfDigits++;
                i /= 10;
            }
            if (numberOfDigits % 2 == 0)
                count++;
        }
        return count;
    }
}
```

---

## ✅ Evaluation of the Submitted Solution

| Aspect              | Assessment                                  |
|---------------------|---------------------------------------------|
| Correctness         | ✅ Handles all valid input correctly         |
| Efficiency          | ✅ Operates in O(N × log D), where D is digits |
| Readability         | ✅ Simple and clear logic                    |
| Memory Efficiency   | ✅ Constant space (O(1))                     |
| Constraint Handling | ✅ Fully complies with input constraints     |

---

## 🧠 Alternative Approach: String Conversion

For slightly cleaner code, one might use string length, though this sacrifices some performance:

```java
class Solution {
    public int findNumbers(int[] nums) {
        int count = 0;
        for (int num : nums) {
            if (String.valueOf(num).length() % 2 == 0) {
                count++;
            }
        }
        return count;
    }
}
```

| Pros         | Cons                          |
|--------------|-------------------------------|
| Readable     | Less performant due to string |
| One-linerish | Allocates extra memory        |

---

## ⏱️ Time and Space Complexity

| Metric           | Value         |
|------------------|---------------|
| Time Complexity  | O(N × log D)  |
| Space Complexity | O(1)          |

---

## 🧾 Final Verdict

| Category        | Verdict                                  |
|------------------|-------------------------------------------|
| Algorithm Style  | ✅ Compliant and optimal                  |
| Code Quality     | ✅ Concise and readable                   |
| Constraint Fit   | ✅ Fully meets all constraints            |
| Recommendation   | ✅ Accepted as-is (no critical changes)   |

> 📌 Your solution is correct, efficient, and adheres to constraints. No revision is necessary.
