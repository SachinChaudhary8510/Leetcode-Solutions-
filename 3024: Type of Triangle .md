# 🚀 LeetCode Problem 3024: Type of Triangle

## 📘 Problem Statement
You are given a **0-indexed** integer array `nums` of size 3 representing side lengths.

- A **triangle is valid** if the sum of any two sides is **strictly greater** than the third side.
- A triangle can be classified as:
  - **Equilateral**: all three sides are equal.
  - **Isosceles**: exactly two sides are equal.
  - **Scalene**: all sides are different.
  
Return the **type of triangle** as a string:  
- `"equilateral"`, `"isosceles"`, `"scalene"`, or `"none"` if the sides **cannot** form a triangle.

---

## 🔍 Examples

### Example 1:
**Input:**  
`nums = [3,3,3]`  

**Output:**  
`"equilateral"`

**Explanation:**  
All sides are equal, forming an equilateral triangle.

---

### Example 2:
**Input:**  
`nums = [3,4,5]`  

**Output:**  
`"scalene"`

**Explanation:**  
- 3 + 4 > 5  
- 3 + 5 > 4  
- 4 + 5 > 3  
All conditions for forming a triangle are satisfied, and no sides are equal — so it's scalene.

---

## 🔒 Constraints
- `nums.length == 3`
- `1 <= nums[i] <= 100`

---

## 💻 Java Solution
```java
class Solution {
    public String triangleType(int[] nums) {
        if (nums[0] + nums[1] <= nums[2] ||
            nums[0] + nums[2] <= nums[1] ||
            nums[1] + nums[2] <= nums[0])
            return "none";
        else if (nums[0] == nums[1] && nums[1] == nums[2])
            return "equilateral";
        else if (nums[0] == nums[1] || nums[1] == nums[2] || nums[0] == nums[2])
            return "isosceles";
        else
            return "scalene";
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def triangleType(self, nums: List[int]) -> str:
        nums.sort()
        if nums[0] + nums[1] <= nums[2]:
            return "none"
        if nums[0] == nums[1] == nums[2]:
            return "equilateral"
        if nums[0] == nums[1] or nums[1] == nums[2] or nums[0] == nums[2]:
            return "isosceles"
        return "scalene"
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    string triangleType(vector<int>& nums) {
        sort(nums.begin(), nums.end());
        if (nums[0] + nums[1] <= nums[2])
            return "none";
        if (nums[0] == nums[1] && nums[1] == nums[2])
            return "equilateral";
        if (nums[0] == nums[1] || nums[1] == nums[2] || nums[0] == nums[2])
            return "isosceles";
        return "scalene";
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(1) — Fixed size array (only 3 elements), constant operations.
- **Space Complexity:** O(1) — No extra space used.

---

## 🌟 Critical Review
Let's be blunt — your solution is **technically correct**, but **lacks robustness** around edge cases.

**Pain points:**
- **Sorting the array first** (`nums.sort()` or equivalent) would have added bulletproof reliability for triangle inequality checks. Without sorting, there’s a risk of misinterpretation for extreme values (even though given constraints are safe here).
- A slightly more defensive coding style would anticipate unexpected input orders and fortify the triangle inequality validation.

In a production-grade environment, **sorting** small fixed-size arrays (3 elements!) is basically a **free safety net** — costing negligible performance but massively boosting code trustworthiness.

---

## 📢 Final Verdict
- **Working?** Yes.
- **Robust?** 90% — Can be 100% with a simple pre-sort.
- **Corporate-grade Solution?** Acceptable but could be refined.
- **Recruiter Impression?** *"Solid, but this candidate assumes happy path inputs a bit too much."*

---

> ✅ **Recommendation:** Sort the side lengths before applying triangle inequality checks for full compliance with rigorous production standards.
