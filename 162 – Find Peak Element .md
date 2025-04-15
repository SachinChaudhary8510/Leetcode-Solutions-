# 🏔️ LeetCode 162 – Find Peak Element

## 📄 Problem Statement

A **peak element** is an element that is **strictly greater than its neighbors**.

Given a **0-indexed integer array** `nums`, find a **peak element**, and return its **index**. If the array contains multiple peaks, return the index to **any** of the peaks.

You may imagine that `nums[-1] = nums[n] = -∞`.  
In other words, an element is always considered to be strictly greater than a neighbor that is outside the array.

### ⏱️ Required Time Complexity: `O(log n)`

---

## 🧠 Examples

### Example 1:
```
Input: nums = [1,2,3,1]
Output: 2
Explanation: 3 is a peak element at index 2.
```

---

### Example 2:
```
Input: nums = [1,2,1,3,5,6,4]
Output: 5
Explanation: Peak elements are 2 (index 1), and 6 (index 5). Either is valid.
```

---

## 📌 Constraints

- `1 <= nums.length <= 1000`  
- `-2³¹ <= nums[i] <= 2³¹ - 1`  
- `nums[i] != nums[i + 1]` for all valid `i`

---

## 💡 Intuition

Linear scan is easy — but not acceptable.

Since you need `O(log n)` time, that’s your cue for **binary search**.  
We compare mid with mid + 1 to determine if we are **ascending or descending** and move accordingly.

---

## 🐍 Python Solution

```python
from typing import List

class Solution:
    def findPeakElement(self, nums: List[int]) -> int:
        left, right = 0, len(nums) - 1
        while left < right:
            mid = (left + right) // 2
            if nums[mid] > nums[mid + 1]:
                right = mid
            else:
                left = mid + 1
        return left
```

---

## 💻 C++ Solution

```cpp
#include <vector>
using namespace std;

class Solution {
public:
    int findPeakElement(vector<int>& nums) {
        int left = 0, right = nums.size() - 1;
        while (left < right) {
            int mid = (left + right) / 2;
            if (nums[mid] > nums[mid + 1])
                right = mid;
            else
                left = mid + 1;
        }
        return left;
    }
};
```

---

## ☕ Java Solution

```java
class Solution {
    public int findPeakElement(int[] nums) {
        if(nums.length == 1)
            return 0;
        else if(nums[0] > nums[1])
            return 0;
        else if(nums[nums.length - 2] < nums[nums.length - 1])
            return nums.length - 1;
        
        for(int i = 1; i < nums.length - 1; i++) {
            if(nums[i-1] < nums[i] && nums[i+1] < nums[i])
                return i;
        }
        return -1;
    }
}
```

### 🔍 Java Analysis

❌ Your solution **works**, but it uses a **linear scan** and does not meet the `O(log n)` requirement.

✅ It handles edge cases and returns a correct index, but it will **not pass time complexity constraints** for larger test cases.

---

## ✅ Time and Space Complexity

| Metric | Complexity |
|--------|------------|
| 🕒 Time | `O(log n)` for binary search solutions |
| 🧠 Space | `O(1)` |

---

## ✨ Summary

This is a **binary search disguised as a peak-finding problem**. The key is to check slope direction and move accordingly. Linear scans are simple, but won’t cut it here. ⛔

---
