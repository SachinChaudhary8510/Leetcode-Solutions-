# 🔍 LeetCode Problem 1913: Maximum Product Difference Between Two Pairs

## 📘 Problem Statement

The **product difference** between two pairs `(a, b)` and `(c, d)` is defined as:

```
(a * b) - (c * d)
```

You are given an integer array `nums`, and your task is to choose four **distinct indices** `w, x, y, z` such that the product difference between the pairs `(nums[w], nums[x])` and `(nums[y], nums[z])` is **maximized**.

**Return** the maximum possible product difference.

---

### 🧠 Examples

#### Example 1:
**Input:**  
`nums = [5,6,2,7,4]`  
**Output:** `34`  
**Explanation:**  
- Choose `(6, 7)` as the first pair → 6 * 7 = 42  
- Choose `(2, 4)` as the second pair → 2 * 4 = 8  
- Product difference: 42 - 8 = **34**

#### Example 2:
**Input:**  
`nums = [4,2,5,9,7,4,8]`  
**Output:** `64`  
**Explanation:**  
- Choose `(9, 8)` → 72  
- Choose `(2, 4)` → 8  
- Product difference: 72 - 8 = **64**

---

### 📚 Constraints

- `4 <= nums.length <= 10⁴`
- `1 <= nums[i] <= 10⁴`

---

## ✅ Java Solution – Brute Force Pair Search

```java
class Solution {
    public int maxProductDifference(int[] nums) {
        int product1 = nums[0] * nums[1];
        int product2 = nums[0] * nums[1];
        
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                int product = nums[i] * nums[j];
                if (product1 < product)
                    product1 = product;
                else if (product2 > product)
                    product2 = product;
            }
        }
        return product1 - product2;
    }
}
```

---

### 🧾 Analysis

| Metric               | Value         |
|----------------------|--------------|
| **Time Complexity**  | O(n²)         |
| **Space Complexity** | O(1)          |
| **Approach**         | Brute force – compare all pairs |

---

## ⚠️ Optimization Note

This brute-force approach works for small arrays but **doesn't scale** for large inputs (e.g., `n = 10⁴`). A far more efficient approach is to **sort the array** and simply use:

```java
return (nums[n - 1] * nums[n - 2]) - (nums[0] * nums[1]);
```

This gives you the **maximum** and **minimum** products in `O(n log n)` time.

### ✅ Optimized Java Version (Recommended)

```java
import java.util.Arrays;

class Solution {
    public int maxProductDifference(int[] nums) {
        Arrays.sort(nums);
        int n = nums.length;
        return (nums[n - 1] * nums[n - 2]) - (nums[0] * nums[1]);
    }
}
```

---

## 🧪 Test Cases

| nums                    | Output | Reason                                   |
|-------------------------|--------|------------------------------------------|
| `[5,6,2,7,4]`           | `34`   | (7×6) - (2×4) = 42 - 8                    |
| `[4,2,5,9,7,4,8]`       | `64`   | (9×8) - (2×4) = 72 - 8                    |
| `[1,2,3,4]`             | `10`   | (4×3) - (1×2) = 12 - 2                    |
| `[100,1,1,1,1,1,1,1]`   | `9900` | (100×1) - (1×1) = 100 - 1 = 99            |

---

## 📌 Conclusion

The problem is essentially about identifying the two largest and two smallest numbers in the array and calculating their product difference. Brute-force is an intuitive starting point, but it lacks the necessary efficiency for competitive settings.

> Always optimize early when input size permits. In this case, **sorting or a single pass max/min scan** will outperform naive nested loops dramatically.

