# 🔍 LeetCode Problem 1550: Three Consecutive Odds

## 📘 Problem Statement

Given an integer array `arr`, determine whether there exist **three consecutive odd numbers** in the array.

Return `true` if such a sequence exists, otherwise return `false`.

---

### 🧠 Examples

#### Example 1:
**Input:** `arr = [2,6,4,1]`  
**Output:** `false`  
**Explanation:** No three consecutive odd numbers.

#### Example 2:
**Input:** `arr = [1,2,34,3,4,5,7,23,12]`  
**Output:** `true`  
**Explanation:** The subarray `[5,7,23]` contains three consecutive odd numbers.

---

### 📚 Constraints

- `1 <= arr.length <= 1000`
- `1 <= arr[i] <= 1000`

---

## ✅ Java Solution – Sliding Count Window

```java
class Solution {
    public boolean threeConsecutiveOdds(int[] arr) {
        int count = 0;
        for (int a : arr) {
            if (a % 2 == 1) {
                count++;
                if (count == 3) {
                    return true;
                }
            } else {
                count = 0;
            }
        }
        return false;
    }
}
```

---

### 🧾 Analysis

| Metric               | Value             |
|----------------------|------------------|
| **Time Complexity**  | O(n)              |
| **Space Complexity** | O(1)              |
| **Approach**         | Linear scan with rolling counter |

---

### ✅ Key Observations

- No need to store state beyond the current streak length.
- Every even number acts as a **reset trigger** for the counter.
- Greedy check for the **minimum window** of 3.

---

## 🧪 Test Cases

| Input                           | Output  | Notes                                 |
|----------------------------------|---------|----------------------------------------|
| `[2,6,4,1]`                      | `false` | No three odds                          |
| `[1,2,34,3,4,5,7,23,12]`        | `true`  | `[5,7,23]` are consecutive odds        |
| `[1,3,5]`                        | `true`  | First three elements qualify           |
| `[2,4,6,8]`                      | `false` | All even numbers                       |
| `[1,1,1,2,3,5]`                 | `true`  | First three values are all odd         |

---

## 📌 Conclusion

This is a straightforward linear scan problem. The key is maintaining minimal state (`count`) and resetting on even elements.

> The algorithm’s elegance lies in its minimalism: no index tracking, no extra memory—just a clean rolling counter.

