
# 🚀LeetCode Problem 485 -  Max Consecutive Ones

**Difficulty**: 🟢 Easy  
**Tags**: Array, Sliding Window  
**Problem Source**: [LeetCode #485](https://leetcode.com/problems/max-consecutive-ones/)

---

## 🧩 Problem Statement

Given a **binary array** `nums`, return the **maximum number of consecutive 1's** in the array.

---

## 🔍 Examples

### Example 1:
```
Input: nums = [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s. The maximum number of consecutive 1s is 3.
```

### Example 2:
```
Input: nums = [1,0,1,1,0,1]
Output: 2
```

---

## ✅ Constraints

- `1 <= nums.length <= 10^5`
- `nums[i]` is either `0` or `1`.

---

## 💡 Java Solution
```java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count = 0;
        int temp = 0;
        for (int i : nums) {
            if (i == 1) {
                temp++;
            } else {
                if (count >= temp)
                    count = count;
                else
                    count = temp;
                temp = 0;
            }
            if (count >= temp)
                count = count;
            else
                count = temp;
        }
        return count;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def findMaxConsecutiveOnes(self, nums):
        count = 0
        temp = 0
        for num in nums:
            if num == 1:
                temp += 1
            else:
                count = max(count, temp)
                temp = 0
        return max(count, temp)
```

---

## 💻 C++ Solution
```cpp
class Solution {
public:
    int findMaxConsecutiveOnes(vector<int>& nums) {
        int count = 0, temp = 0;
        for (int n : nums) {
            if (n == 1) {
                temp++;
            } else {
                count = max(count, temp);
                temp = 0;
            }
        }
        return max(count, temp);
    }
};
```

---

## 📦 How to Run

Make sure your project has these files:
```
📁 MaxConsecutiveOnes
├── Solution.java
├── solution.py
├── solution.cpp
└── README.md ✅
```

---

## 📬 Contribute

Feel free to open a pull request if you have a better solution or want to add optimizations! 💪

---

## 🏁 Happy Coding!
