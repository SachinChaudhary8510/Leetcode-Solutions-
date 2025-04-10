# 🎯 LeetCode 3467 - Transform Array by Parity

## 🧠 Problem Statement

You are given an **integer array `nums`**. Transform `nums` by performing the following operations in **exact order**:

1. Replace each **even number** with `0`.
2. Replace each **odd number** with `1`.
3. **Sort** the modified array in **non-decreasing** order.

🔁 **Return** the resulting array after performing these operations.

---

## 🧪 Examples

### ✅ Example 1:

**Input:**  
`nums = [4,3,2,1]`  
**Output:**  
`[0,0,1,1]`  

**Explanation:**  
- Replace even numbers → `[0,1,0,1]`  
- Sort → `[0,0,1,1]`

---

### ✅ Example 2:

**Input:**  
`nums = [1,5,1,4,2]`  
**Output:**  
`[0,0,1,1,1]`

**Explanation:**  
- Replace even numbers → `[1,1,1,0,0]`  
- Sort → `[0,0,1,1,1]`

---

## 📚 Constraints

- `1 <= nums.length <= 100`
- `1 <= nums[i] <= 1000`

---

## 💻 Java Solution
```java
class Solution {
    public int[] transformArray(int[] nums) {
        int count = 0;
        int[] a = new int[nums.length];
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] % 2 == 1) count++;
        }
        for (int i = 0; i < count; i++) {
            a[a.length - 1 - i] = 1;
        }
        return a;
    }
}
```
## 🐍 Python Solution
python
```
Edit
class Solution:
    def transformArray(self, nums):
        transformed = [1 if x % 2 else 0 for x in nums]
        transformed.sort()
        return transformed
```
💻 C++ Solution
cpp
```
Edit
class Solution {
public:
    vector<int> transformArray(vector<int>& nums) {
        vector<int> res;
        for (int num : nums)
            res.push_back(num % 2 ? 1 : 0);
        sort(res.begin(), res.end());
        return res;
    }
};
```
## ⏱️ Time & Space Complexity
Approach	Time Complexity	Space Complexity
All Solutions	`O(n log n)`	`O(n)`
Transform pass is `O(n)`

Sort pass is `O(n log n)`

Extra space used to store result array

## 🌟 Key Takeaways
-`Understand array mutation techniques`

-`Reinforce transformation + sorting logic`

-`Excellent beginner-level problem that teaches sequencing of transformations`
