# 🚀 LeetCode 1920 - Build Array from Permutation

## 🧠 Problem Statement

> Given a **zero-based permutation** `nums` (0-indexed), build an array `ans` of the same length where `ans[i] = nums[nums[i]]` for each `0 <= i < nums.length` and return it.

A zero-based permutation `nums` is an array of **distinct** integers from `0` to `nums.length - 1` (inclusive).

---

## 📥 Examples

### ✅ Example 1:
**Input:** `nums = [0,2,1,5,3,4]`  
**Output:** `ans = [0,1,2,4,5,3]`  
**Explanation:**  
ans = [nums[nums[0]], nums[nums[1]], nums[nums[2]], nums[nums[3]], nums[nums[4]], nums[nums[5]]] = [nums[0], nums[2], nums[1], nums[5], nums[3], nums[4]] = [0,1,2,4,5,3]

markdown
Always show details

Copy

### ✅ Example 2:
**Input:** `nums = [5,0,1,2,3,4]`  
**Output:** `ans = [4,5,0,1,2,3]`  
**Explanation:**  
ans = [nums[nums[0]], nums[nums[1]], nums[nums[2]], nums[nums[3]], nums[nums[4]], nums[nums[5]]] = [nums[5], nums[0], nums[1], nums[2], nums[3], nums[4]] = [4,5,0,1,2,3]

yaml
Always show details

Copy

---


## 🔒 Constraints
- `1 <= nums.length <= 1000`
- `0 <= nums[i] < nums.length`
- The elements in `nums` are **distinct**

---


## 🧮 Java Solution
```java
class Solution {
    public int[] buildArray(int[] nums) {
        int[] ans = new int[nums.length];
        for(int i = 0; i< nums.length; i++){
            ans[i] = nums[nums[i]];
        }
        return ans;
    }
}
```
## 🐍 Python Solution
python
Always show details

```
class Solution:
    def buildArray(self, nums):
        return [nums[nums[i]] for i in range(len(nums))]
```
## 💻 C++ Solution
cpp
Always show details

```
class Solution {
public:
    vector<int> buildArray(vector<int>& nums) {
        vector<int> ans(nums.size());
        for(int i = 0; i < nums.size(); i++) {
            ans[i] = nums[nums[i]];
        }
        return ans;
    }
};
```
## ⏱️ Time & Space Complexity
Algorithm	Time Complexity	Space Complexity
All Approaches	`O(n)` `O(n)`
## ✅ Key Takeaways
This is a direct application of array indexing.

The key is to understand zero-based permutation.

Useful for practicing array manipulation and indexing.

🧲 Tags
`Array`  `Simulation`  `Index Manipulation`
