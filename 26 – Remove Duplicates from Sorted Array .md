# 🧹 LeetCode 26 – Remove Duplicates from Sorted Array

## 📄 Problem Statement

You are given an **integer array `nums`** sorted in **non-decreasing order**.  
Your task is to **remove the duplicates in-place**, such that each **unique element appears only once**, and return the number of unique elements.

📝 You **must not allocate extra space** for another array — you **must modify the input array in-place** and use **O(1) extra memory**.

The **number of unique elements** is denoted as `k`.  
The first `k` elements of `nums` should hold the **final result**, and the rest of the array doesn't matter.

---

## 🧠 Examples

### Example 1:
```
Input: nums = [1,1,2]
Output: 2, nums = [1,2,_]
```
✅ Return `k = 2`. The first 2 elements `[1,2]` are the unique ones.

---

### Example 2:
```
Input: nums = [0,0,1,1,1,2,2,3,3,4]
Output: 5, nums = [0,1,2,3,4,_,_,_,_,_]
```
✅ Return `k = 5`. The unique values are `[0,1,2,3,4]`.

---

## 📌 Constraints

- `1 <= nums.length <= 3 × 10⁴`  
- `-100 <= nums[i] <= 100`  
- `nums` is **sorted** in **non-decreasing order**

---

## 💡 Intuition

Because the array is **sorted**, **duplicates will be adjacent**.  
We can iterate with a pointer and **overwrite duplicates** with the next new value we find.  
The goal is to modify the original array in-place without using additional space.

---

## 🐍 Python Solution

```python
from typing import List

class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if not nums:
            return 0

        k = 1  # Pointer for next unique value
        for i in range(1, len(nums)):
            if nums[i] != nums[i - 1]:
                nums[k] = nums[i]
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
    int removeDuplicates(vector<int>& nums) {
        if (nums.empty()) return 0;

        int k = 1;
        for (int i = 1; i < nums.size(); ++i) {
            if (nums[i] != nums[i - 1]) {
                nums[k] = nums[i];
                ++k;
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
    public int removeDuplicates(int[] nums) {
        int count = 0;
        int[] a = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (i == 0 || nums[i] != nums[i - 1]) {
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

🔍 **Problem**: This solution **uses O(n) extra space** via the `a[]` array, which violates the in-place constraint.  
❌ **Not acceptable for interviews or strict in-place requirements** like LeetCode.  
✔️ **Correct logic**, but space complexity disqualifies it.

### ✅ Recommended Fix:

Use a single pointer to overwrite duplicates directly in `nums[]`:
```java
class Solution {
    public int removeDuplicates(int[] nums) {
        if (nums.length == 0) return 0;

        int k = 1;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] != nums[i - 1]) {
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

## 🔚 Summary

This is a classic **in-place overwrite** problem on sorted arrays.  
Don't get tempted to use extra arrays or sets — interviews will penalize that.  
Stick to a clean **two-pointer approach** for optimal performance and correctness. 💼

---
