# 🚀 LeetCode Problem 1672: Richest Customer Wealth

## 📘 Problem Statement
You are given an `m x n` integer grid `accounts`, where `accounts[i][j]` represents the amount of money the `i-th` customer has in the `j-th` bank account.  
Return **the wealth** that the richest customer has.

A customer's wealth is the sum of money they have in **all** their bank accounts.  
The richest customer is the customer with the **maximum** total wealth.

---

## 🔍 Examples

### Example 1:
**Input:**  
`accounts = [[1,2,3],[3,2,1]]`  
**Output:**  
`6`  
**Explanation:**  
- 1st customer wealth = `1 + 2 + 3 = 6`
- 2nd customer wealth = `3 + 2 + 1 = 6`
- Both customers are equally rich. Return `6`.

---

### Example 2:
**Input:**  
`accounts = [[1,5],[7,3],[3,5]]`  
**Output:**  
`10`  
**Explanation:**  
- 1st customer wealth = `6`
- 2nd customer wealth = `10`
- 3rd customer wealth = `8`
- Richest customer wealth = `10`.

---

### Example 3:
**Input:**  
`accounts = [[2,8,7],[7,1,3],[1,9,5]]`  
**Output:**  
`17`  
**Explanation:**  
- 1st customer wealth = `17`
- 2nd customer wealth = `11`
- 3rd customer wealth = `15`
- Richest customer wealth = `17`.

---

## 🔒 Constraints
- `m == accounts.length`
- `n == accounts[i].length`
- `1 <= m, n <= 50`
- `1 <= accounts[i][j] <= 100`

---

## 💻 Java Solution
```java
class Solution {
    public int maximumWealth(int[][] accounts) {
        int result = 0;
        for (int i = 0; i < accounts.length; i++) {
            int sum = 0;
            for (int j = 0; j < accounts[i].length; j++) {
                sum += accounts[i][j];
            }
            if (sum > result) {
                result = sum;
            }
        }
        return result;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        return max(sum(customer) for customer in accounts)
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int maximumWealth(vector<vector<int>>& accounts) {
        int result = 0;
        for (auto& customer : accounts) {
            int sum = 0;
            for (int money : customer) {
                sum += money;
            }
            result = max(result, sum);
        }
        return result;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(m × n) — Each account is visited exactly once.
- **Space Complexity:** O(1) — Only a few variables are used regardless of input size.

---

## 🌟 Summary
This problem evaluates the ability to **traverse a 2D matrix** efficiently and calculate simple aggregates like a row sum.  
It's a classic example where overcomplicating the solution would be a red flag 🚩 during a real-world system design or coding interview.
