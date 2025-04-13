# 🚀 LeetCode 3065 – Minimum Operations to Exceed Threshold Value I

## 📄 Problem Statement

You are given a **0-indexed integer array** `nums`, and an integer `k`.

In **one operation**, you can **remove one occurrence of the smallest element** of `nums`.

Return the **minimum number of operations** needed so that **all elements of the array are greater than or equal to `k`**.

---

## 🧠 Examples

### Example 1:
```
Input: nums = [2,11,10,1,3], k = 10  
Output: 3  
```
➡️ Remove elements `< 10`: [2, 1, 3] → total 3 operations.

---

### Example 2:
```
Input: nums = [1,1,2,4,9], k = 1  
Output: 0  
```
✅ All elements already ≥ 1, so no operation needed.

---

### Example 3:
```
Input: nums = [1,1,2,4,9], k = 9  
Output: 4  
```
🗑️ Remove [1, 1, 2, 4] → 4 operations required.

---

## 📌 Constraints

- `1 <= nums.length <= 50`  
- `1 <= nums[i] <= 10⁹`  
- `1 <= k <= 10⁹`  
- It is **guaranteed** that at least **one** element in `nums` is `>= k`

---

## 💡 Intuition

Only elements **less than `k`** can be removed. Each such element requires **1 operation**.  
So, count how many elements are `< k` – that’s your answer.

---

## 🐍 Python Solution

```python
from typing import List

class Solution:
    def minOperations(self, nums: List[int], k: int) -> int:
        return sum(1 for num in nums if num < k)
```

---

## 💻 C++ Solution

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int minOperations(vector<int>& nums, int k) {
        int count = 0;
        for (int num : nums) {
            if (num < k) count++;
        }
        return count;
    }
};
```

---

## ☕ Java Solution

```java
class Solution {
    public int minOperations(int[] nums, int k) {
        int count = 0;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] < k)
                count++;
        }
        return count;
    }
}
```

---

## ✅ Time and Space Complexity

| Metric | Complexity |
|--------|------------|
| 🕒 Time | `O(n)` — One pass through array |
| 🧠 Space | `O(1)` — Constant extra space |

---

## 🔚 Summary

This is a classic **filter and count** problem — no need for sorting, heaps, or fancy data structures. Just focus on what you can remove and count efficiently. 💼

---
