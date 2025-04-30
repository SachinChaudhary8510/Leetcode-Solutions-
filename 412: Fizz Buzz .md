# 🔢 LeetCode Problem 412: Fizz Buzz

## 📘 Problem Statement

Given an integer `n`, return a string array `answer` (1-indexed) where:

- `answer[i] == "FizzBuzz"` if `i` is divisible by **both** 3 and 5.
- `answer[i] == "Fizz"` if `i` is divisible by **3 only**.
- `answer[i] == "Buzz"` if `i` is divisible by **5 only**.
- `answer[i] == i` (as a string) otherwise.

---

## 🧪 Examples

### Example 1:
**Input:** `n = 3`  
**Output:** `["1", "2", "Fizz"]`

### Example 2:
**Input:** `n = 5`  
**Output:** `["1", "2", "Fizz", "4", "Buzz"]`

### Example 3:
**Input:** `n = 15`  
**Output:**  
`["1", "2", "Fizz", "4", "Buzz", "Fizz", "7", "8", "Fizz", "Buzz", "11", "Fizz", "13", "14", "FizzBuzz"]`

---

## 🔒 Constraints

- \( 1 \leq n \leq 10^4 \)

---

## 💻 Java Solution

```java
class Solution {
    public List<String> fizzBuzz(int n) {
        List<String> a = new ArrayList<>();

        for (int i = 1; i <= n; i++) {
            if (i % 3 == 0 && i % 5 == 0) {
                a.add("FizzBuzz");
            } else if (i % 3 == 0) {
                a.add("Fizz");
            } else if (i % 5 == 0) {
                a.add("Buzz");
            } else {
                a.add(String.valueOf(i));
            }
        }

        return a;
    }
}
```

---

## ✅ Evaluation of the Submitted Solution

| Criteria             | Assessment                                  |
|----------------------|----------------------------------------------|
| **Correctness**       | ✅ 100% accurate                             |
| **Clarity**           | ✅ Clear and maintainable                    |
| **Performance**       | ✅ O(n) time, O(n) space — optimal            |
| **Edge Case Handling**| ✅ Works for lower/upper bounds               |
| **Design**            | ✅ Proper use of List, String.valueOf         |

---

## 🧠 Alternative Approach (Optional)

You could optimize string concatenation slightly with a `StringBuilder` or use precomputed modulus arrays if pushing toward micro-optimization (rarely necessary here).

---

## ⏱️ Time and Space Complexity

| Metric           | Value  |
|------------------|--------|
| Time Complexity  | O(n)   |
| Space Complexity | O(n)   |

---

## 🧾 Final Verdict

| Category        | Verdict                            |
|------------------|-------------------------------------|
| Code Quality     | ✅ Clean and correct                |
| Algorithm Choice | ✅ Matches optimal for problem      |
| Suggested Change | ❌ None needed                     |
| Production Ready | ✅ Absolutely                       |

> 🔎 Your implementation is precise, idiomatic, and efficiently handles all input sizes up to the maximum constraint. Approved without reservations.
