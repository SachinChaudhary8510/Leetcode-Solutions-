# 🚀 LeetCode Problem 3232: Find if Digit Game Can Be Won

## 📘 Problem Statement
You are given an array of positive integers `nums`.

- **Alice and Bob** are playing a game:
  - Alice can choose **either all single-digit numbers** or **all double-digit numbers** from `nums`.
  - Bob receives the remaining numbers.
- **Victory Condition**:  
  Alice wins **if and only if** the sum of her numbers is **strictly greater** than the sum of Bob’s numbers.

Return `true` if Alice can win, otherwise return `false`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`nums = [1,2,3,4,10]`  

**Output:**  
`false`  

**Explanation:**  
- Single-digit sum = 1+2+3+4 = 10  
- Double-digit sum = 10  
Neither option gives Alice a strictly greater sum.

---

### Example 2:
**Input:**  
`nums = [1,2,3,4,5,14]`  

**Output:**  
`true`  

**Explanation:**  
- Single-digit sum = 1+2+3+4+5 = 15  
- Double-digit sum = 14  
Choosing **single-digit numbers**, Alice wins (15 > 14).

---

### Example 3:
**Input:**  
`nums = [5,5,5,25]`  

**Output:**  
`true`  

**Explanation:**  
- Single-digit sum = 5+5+5 = 15  
- Double-digit sum = 25  
Choosing **double-digit numbers**, Alice wins (25 > 15).

---

## 🔒 Constraints
- `1 <= nums.length <= 100`
- `1 <= nums[i] <= 99`

---

## 💻 Java Solution
```java
class Solution {
    public boolean canAliceWin(int[] nums) {
        int sum1 = 0;
        int sum2 = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] > 9)
                sum1 += nums[i];
            else
                sum2 += nums[i];
        }
        return sum1 != sum2;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def canAliceWin(self, nums: List[int]) -> bool:
        sum_single = sum(num for num in nums if num <= 9)
        sum_double = sum(num for num in nums if num >= 10)
        return sum_single > sum_double or sum_double > sum_single
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    bool canAliceWin(vector<int>& nums) {
        int sumSingle = 0, sumDouble = 0;
        for (int num : nums) {
            if (num <= 9)
                sumSingle += num;
            else
                sumDouble += num;
        }
        return sumSingle != sumDouble;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(N) — where N is the number of elements in `nums`, due to single traversal.
- **Space Complexity:** O(1) — constant space, no additional data structures are used.

---

## 🌟 Critical Review
Frankly speaking, your Java solution is correct but **marginally misleading** in intent.

> Your condition `sum1 != sum2` **does not** *explicitly* check for "strictly greater" — it just checks if sums are unequal, which risks missing problem nuances in stricter validation environments.

**Correct logic should be:**  
- Check if either `sum of single-digit numbers > sum of double-digit numbers`  
- Or `sum of double-digit numbers > sum of single-digit numbers`

In short — **inequality (`!=`) is a half-baked shortcut.**
👉 In professional coding, shortcuts that bypass the problem description literally will get you penalized in reviews.

---

## 📢 Final Verdict
- **Working?** Yes.
- **Robust?** No.
- **Corporate-grade Solution?** Not really. Needs explicit greater-than checks for critical reliability.  
- **Recruiter Impression?** *"Candidate might skip over critical conditions under pressure."*

--- 

> ✅ Recommendation: Explicitly compare sums using `>` rather than relying on `!=` for maximum clarity and auditability in professional codebases.
