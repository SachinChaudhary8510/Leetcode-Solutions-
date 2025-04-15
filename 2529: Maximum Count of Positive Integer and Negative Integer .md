
# 🚀 LeetCode Problem 2529: Maximum Count of Positive Integer and Negative Integer

## 📘 Problem Statement

Given an array `nums` **sorted in non-decreasing order**, return the maximum between the number of **positive integers** and the number of **negative integers**.

In other words, if the number of positive integers in `nums` is `pos` and the number of negative integers is `neg`, then return the maximum of `pos` and `neg`.

📌 Note: `0` is **neither positive nor negative**.

---

## 🔍 Examples

### Example 1:

**Input:**  
nums = [-2, -1, -1, 1, 2, 3]  
**Output:** 3  
**Explanation:**  
There are 3 positive integers and 3 negative integers. The maximum count among them is 3.

---

### Example 2:

**Input:**  
nums = [-3, -2, -1, 0, 0, 1, 2]  
**Output:** 3  
**Explanation:**  
There are 3 negative integers and 2 positive integers. The maximum count among them is 3.

---

### Example 3:

**Input:**  
nums = [5, 20, 66, 1314]  
**Output:** 4  
**Explanation:**  
There are 4 positive integers and 0 negative integers. The maximum count among them is 4.

---

## 🔒 Constraints

- `1 <= nums.length <= 2000`
- `-2000 <= nums[i] <= 2000`
- `nums` is sorted in non-decreasing order.

---

## 💻 Java Solution

```java
class Solution {
    public int maximumCount(int[] nums) {
        int countp = 0;
        int countn = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] < 0)
                countn++;
            if (nums[i] > 0)
                countp++;
        }
        return (countp >= countn) ? countp : countn;
    }
}
```

---

## 🐍 Python Solution

```python
class Solution:
    def maximumCount(self, nums):
        pos = sum(1 for x in nums if x > 0)
        neg = sum(1 for x in nums if x < 0)
        return max(pos, neg)
```

---

## 💠 C++ Solution

```cpp
class Solution {
public:
    int maximumCount(vector<int>& nums) {
        int pos = 0, neg = 0;
        for (int num : nums) {
            if (num > 0) pos++;
            else if (num < 0) neg++;
        }
        return max(pos, neg);
    }
};
```

---

## ⏱️ Time and Space Complexity

- **Time Complexity:** O(n), where `n` is the length of `nums`
- **Space Complexity:** O(1)

---

## 🌟 Summary

This problem evaluates fundamental understanding of array traversal and conditional logic. The key is to correctly count positive and negative values while ignoring zeros.
