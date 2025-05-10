# ⚖️ LeetCode Problem 2918: Minimum Equal Sum of Two Arrays After Replacing Zeros

## 📘 Problem Statement

You are given two arrays `nums1` and `nums2` consisting of **positive integers** and possibly some `0`s.

You must replace **all zeros** in both arrays with **strictly positive integers** such that:
- The **sum of both arrays becomes equal**.

🔁 Return the **minimum equal sum** you can obtain, or `-1` if making the sums equal is **impossible**.

---

### 🧠 Examples

#### Example 1:
**Input:** `nums1 = [3,2,0,1,0]`, `nums2 = [6,5,0]`  
**Output:** `12`  
**Explanation:**
- Replace zeros in `nums1` with `[2,4]` ⇒ `nums1 = [3,2,2,1,4]`, sum = 12
- Replace zero in `nums2` with `1` ⇒ `nums2 = [6,5,1]`, sum = 12

#### Example 2:
**Input:** `nums1 = [2,0,2,0]`, `nums2 = [1,4]`  
**Output:** `-1`  
**Explanation:**  
Even with optimal replacements, it's impossible to equalize the sums.

---

### 📚 Constraints

- `1 <= nums1.length, nums2.length <= 10⁵`
- `0 <= nums1[i], nums2[i] <= 10⁶`

---

## ✅ Java Solution – Greedy + Case Handling

```java
class Solution {
    public long minSum(int[] nums1, int[] nums2) {
        long count1 = 0;
        long count2 = 0;
        long sum1 = 0;
        long sum2 = 0;

        for (int num : nums1) {
            if (num == 0) count1++;
            else sum1 += num;
        }

        for (int num : nums2) {
            if (num == 0) count2++;
            else sum2 += num;
        }

        if (count1 != 0 && count2 != 0) {
            return Math.max(sum1 + count1, sum2 + count2);
        } else if (count1 != 0 && count2 == 0) {
            return (sum1 + count1 > sum2) ? -1 : sum2;
        } else if (count1 == 0 && count2 != 0) {
            return (sum2 + count2 > sum1) ? -1 : sum1;
        } else {
            return (sum1 == sum2) ? sum1 : -1;
        }
    }
}
```

---

### 🧾 Analysis

| Metric               | Value             |
|----------------------|------------------|
| **Time Complexity**  | O(n)              |
| **Space Complexity** | O(1)              |
| **Approach**         | Greedy + Case-by-case |

---

### ✅ Key Observations

- To **minimize the total sum**, always replace zeros with **1**, the smallest valid number.
- Case analysis:
  - **Both arrays have zeros:** Maximize the smaller potential sum to match the higher.
  - **Only one array has zeros:** You can only try to match its increased minimum sum to the other; otherwise return `-1`.
  - **No zeros:** If sums match, return it; else `-1`.

---

## 🧪 Test Cases

| nums1                   | nums2         | Output | Notes                                    |
|-------------------------|---------------|--------|------------------------------------------|
| `[3,2,0,1,0]`           | `[6,5,0]`     | `12`   | Replace with `[2,4]` and `1`             |
| `[2,0,2,0]`             | `[1,4]`       | `-1`   | No valid configuration                  |
| `[0,0,0]`               | `[0,0,0]`     | `3`    | Replace all with `1`s                   |
| `[0]`                   | `[100]`       | `100`  | Replace 0 with 100                       |
| `[0]`                   | `[1]`         | `-1`   | Cannot reduce sum of `[0]` to match `[1]` |

---

## 📌 Conclusion

This problem is an **edge-case-heavy greedy simulation**, requiring:
- Awareness of minimum values for replacement
- Careful distinction between mutually exclusive cases
- Avoidance of overfitting to symmetric behavior

> If both arrays have zeros, you control both sides of the equation. If only one does, you're at its mercy. That’s the key constraint.

