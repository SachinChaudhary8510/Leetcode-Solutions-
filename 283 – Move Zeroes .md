# 🧱 LeetCode 283 – Move Zeroes

## 📄 Problem Statement

Given an **integer array** `nums`, move all `0`'s to the **end** of it while maintaining the **relative order** of the non-zero elements.

⚠️ You **must do this in-place**, without making a copy of the array.

---

## 🧠 Examples

### Example 1:
```
Input: nums = [0,1,0,3,12]
Output: [1,3,12,0,0]
```

➡️ Non-zero elements kept in order, zeroes pushed to the end.

---

### Example 2:
```
Input: nums = [0]
Output: [0]
```

✅ Nothing to move.

---

## 📌 Constraints

- `1 <= nums.length <= 10⁴`  
- `-2³¹ <= nums[i] <= 2³¹ - 1`  

---

## 💡 Intuition

You want to keep the **relative order of non-zero elements**, and **move all zeros to the back**.  

➡️ Solution: Use a **write pointer** to fill non-zero elements, then fill the rest with zeroes.

---

## 🐍 Python Solution

```python
from typing import List

class Solution:
    def moveZeroes(self, nums: List[int]) -> None:
        k = 0
        for num in nums:
            if num != 0:
                nums[k] = num
                k += 1
        for i in range(k, len(nums)):
            nums[i] = 0
```

---

## 💻 C++ Solution

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int k = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != 0) {
                nums[k++] = nums[i];
            }
        }
        for (int i = k; i < nums.size(); i++) {
            nums[i] = 0;
        }
    }
};
```

---

## ☕ Java Solution

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int[] a = new int[nums.length];  // ❌ Extra space used (not allowed in-place)
        int k = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[k] = nums[i];
                k++;
            }
        }
        for (int i = k; i < nums.length; i++) {
            nums[i] = 0;
        }
    }
}
```

### 🔍 Java Analysis

Your logic is **correct**, but you're **violating the space constraint** by creating a new array `a[]`. The good news: you **didn’t actually use it**, so this solution works fine **as-is**, but the declaration is unnecessary.

---

## ✅ Time and Space Complexity

| Metric | Complexity |
|--------|------------|
| 🕒 Time | `O(n)`     |
| 🧠 Space | `O(1)` ✅ (after removing unused array) |

---

## ✔️ Corrected Java (Cleaned)

```java
class Solution {
    public void moveZeroes(int[] nums) {
        int k = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 0) {
                nums[k++] = nums[i];
            }
        }
        for (int i = k; i < nums.length; i++) {
            nums[i] = 0;
        }
    }
}
```

---

## 🧾 Summary

This is a textbook **in-place overwrite** problem — track non-zero values, then pad with zeroes. 💡  
Avoid creating new arrays unless absolutely necessary — especially when the problem emphasizes *in-place*.

---
