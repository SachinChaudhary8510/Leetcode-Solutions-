# ❌ LeetCode 27 – Remove Element

## 📄 Problem Statement

Given an **integer array** `nums` and an **integer value** `val`, remove **all occurrences** of `val` in-place.  
The **order of elements may be changed**, and you should return the number of elements **not equal** to `val`.

Only the first `k` elements of `nums` (those **not equal to `val`**) matter.  
The rest of the array is **irrelevant**.

---

## 🧠 Examples

### Example 1:
```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
```
✅ Return `k = 2`. The remaining 2s are kept.

---

### Example 2:
```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
```
✅ Return `k = 5`. Elements not equal to 2 are moved to the front.

---

## 📌 Constraints

- `0 <= nums.length <= 100`  
- `0 <= nums[i] <= 50`  
- `0 <= val <= 100`  

---

## 💡 Intuition

We're allowed to modify the array **in any order**, so the key is to **overwrite** the values equal to `val` with valid ones.

We use a **write pointer** to track the next available position for a valid element.

---

## 🐍 Python Solution

```python
from typing import List

class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        k = 0
        for num in nums:
            if num != val:
                nums[k] = num
                k += 1
        return k
```

---

## 💻 C++ Solution

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int k = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
};
```

---

## ☕ Java Solution

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count = 0;
        int[] a = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                a[count] = nums[i];
                count++;
            }
        }
        for (int i = 0; i < count; i++) {
            nums[i] = a[i];
        }
        return count;
    }
}
```

### 🧪 Java Analysis

🔍 **Problem**: This approach uses **O(n)** extra space (array `a[]`), which violates the **in-place** constraint.  
✅ **Correct logic**, but **not acceptable** for real-world interviews or strict in-place environments.

---

## ✔️ Improved Java Solution

```java
class Solution {
    public int removeElement(int[] nums, int val) {
        int k = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != val) {
                nums[k] = nums[i];
                k++;
            }
        }
        return k;
    }
}
```

---

## ✅ Time and Space Complexity

| Metric            | Complexity  |
|-------------------|-------------|
| 🕒 Time            | `O(n)`      |
| 🧠 Space (Correct) | `O(1)`      |
| 🧠 Space (Your Java) | ❌ `O(n)` due to auxiliary array |

---

## 🧾 Summary

This problem emphasizes **in-place modification** with no memory overhead.  
Use the **overwrite technique** to fill from the front as you go.  
Avoid using extra arrays or lists, as they defeat the core constraint. 💼

---
