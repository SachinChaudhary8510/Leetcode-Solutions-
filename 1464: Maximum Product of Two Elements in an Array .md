# 🚀 LeetCode Problem 1464: Maximum Product of Two Elements in an Array

## 📘 Problem Statement
Given an array of integers `nums`, select two **different** indices `i` and `j`, and return the **maximum value** of:

> `(nums[i] - 1) * (nums[j] - 1)`

---

## 🔍 Examples

### Example 1:
**Input:**  
`nums = [3,4,5,2]`  
**Output:**  
`12`  
**Explanation:**  
Choosing `i = 1` and `j = 2`, we have:  
`(nums[1] - 1) * (nums[2] - 1) = (4-1)*(5-1) = 3*4 = 12`.

---

### Example 2:
**Input:**  
`nums = [1,5,4,5]`  
**Output:**  
`16`  
**Explanation:**  
Choosing `i = 1` and `j = 3`, we get:  
`(5-1)*(5-1) = 4*4 = 16`.

---

### Example 3:
**Input:**  
`nums = [3,7]`  
**Output:**  
`12`  
**Explanation:**  
`(3-1)*(7-1) = 2*6 = 12`.

---

## 🔒 Constraints
- `2 <= nums.length <= 500`
- `1 <= nums[i] <= 10³`

---

## 💻 Java Solution
```java
class Solution {
    public int maxProduct(int[] nums) {
        int num1 = nums[0];
        int num2 = 0;
        for (int i = 1; i < nums.length; i++) {
            if (nums[i] >= num1) {
                num2 = num1;
                num1 = nums[i];
            } else if (nums[i] > num2) {
                num2 = nums[i];
            }
        }
        return (num1 - 1) * (num2 - 1);
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def maxProduct(self, nums: List[int]) -> int:
        first = second = 0
        for num in nums:
            if num > first:
                second = first
                first = num
            elif num > second:
                second = num
        return (first - 1) * (second - 1)
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int maxProduct(vector<int>& nums) {
        int first = 0, second = 0;
        for (int num : nums) {
            if (num > first) {
                second = first;
                first = num;
            } else if (num > second) {
                second = num;
            }
        }
        return (first - 1) * (second - 1);
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(n) — One pass through the array.
- **Space Complexity:** O(1) — Only constant extra space is used.

---

## 🌟 Summary
This problem checks if you understand how to **track two maximums** efficiently.  
Sorting is overkill here; you only need **one linear scan**, demonstrating fundamental optimization principles expected in production-quality code.
