# 🚀 LeetCode Problem 1470: Shuffle the Array

## 📘 Problem Statement
Given the array `nums` consisting of `2n` elements in the form `[x1,x2,...,xn,y1,y2,...,yn]`, return the array in the form `[x1,y1,x2,y2,...,xn,yn]`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`nums = [2,5,1,3,4,7], n = 3`  
**Output:**  
`[2,3,5,4,1,7]`  
**Explanation:**  
Since `x1=2`, `x2=5`, `x3=1`, `y1=3`, `y2=4`, `y3=7`, the output is `[2,3,5,4,1,7]`.

---

### Example 2:
**Input:**  
`nums = [1,2,3,4,4,3,2,1], n = 4`  
**Output:**  
`[1,4,2,3,3,2,4,1]`

---

### Example 3:
**Input:**  
`nums = [1,1,2,2], n = 2`  
**Output:**  
`[1,2,1,2]`

---

## 🔒 Constraints
- `1 <= n <= 500`  
- `nums.length == 2n`  
- `1 <= nums[i] <= 10³`

---

## 💻 Java Solution
```java
class Solution {
    public int[] shuffle(int[] nums, int n) {
        int[] a = new int[nums.length];
        int count = 0;
        for (int i = 0; i < n; i++) {
            a[count] = nums[i];
            a[count + 1] = nums[n + i];
            count += 2;
        }
        return a;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def shuffle(self, nums: List[int], n: int) -> List[int]:
        result = []
        for i in range(n):
            result.append(nums[i])
            result.append(nums[n + i])
        return result
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    vector<int> shuffle(vector<int>& nums, int n) {
        vector<int> result;
        for (int i = 0; i < n; ++i) {
            result.push_back(nums[i]);
            result.push_back(nums[n + i]);
        }
        return result;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(n)  
- **Space Complexity:** O(n)

---

## 🌟 Summary
This problem tests basic array manipulation. It’s essential to understand index-based partitioning and proper recombination, which is common in problems involving paired input or structured transformation.
