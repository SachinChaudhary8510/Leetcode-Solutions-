# 🚛 LeetCode Problem 2739: Total Distance Traveled

## 📘 Problem Statement
You are given:
- `mainTank`: liters of fuel in the main tank.
- `additionalTank`: liters of fuel in the additional tank.

**Mechanics:**
- The truck drives **10 km per liter** of fuel.
- After **every 5 liters** consumed from the main tank:
  - If there is at least **1 liter** available in the additional tank, **1 liter** is transferred immediately into the main tank.
- Transfers are **discrete**, not continuous.

**Objective:**  
Return the **maximum distance** the truck can travel.

---

## 🔍 Examples

### Example 1:
**Input:**  
`mainTank = 5`, `additionalTank = 10`  

**Output:**  
`60`

**Explanation:**  
- Spend 5 liters ➔ mainTank becomes 0, transfer 1 liter from additional ➔ mainTank becomes 1 liter ➔ Distance = 50 km.
- Spend 1 liter ➔ mainTank becomes 0 ➔ Distance += 10 km.
- **Total Distance = 60 km.**

---

### Example 2:
**Input:**  
`mainTank = 1`, `additionalTank = 2`  

**Output:**  
`10`

**Explanation:**  
- Spend 1 liter ➔ mainTank becomes 0 ➔ Distance = 10 km.

---

## 🔒 Constraints
- `1 <= mainTank, additionalTank <= 100`
- All fuel consumption and transfer events are instantaneous after every 5 liters.

---

## 💻 Java Solution
```java
class Solution {
    public int distanceTraveled(int mainTank, int additionalTank) {
        int distance = 0;
        while (mainTank >= 5) {
            mainTank -= 5;
            if (additionalTank > 0) {
                mainTank++;
                additionalTank--;
                distance += 50;
            } else {
                distance += 50;
            }
        }
        distance += mainTank * 10;
        return distance;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def distanceTraveled(self, mainTank: int, additionalTank: int) -> int:
        distance = 0
        while mainTank >= 5:
            mainTank -= 5
            if additionalTank > 0:
                mainTank += 1
                additionalTank -= 1
            distance += 50
        distance += mainTank * 10
        return distance
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    int distanceTraveled(int mainTank, int additionalTank) {
        int distance = 0;
        while (mainTank >= 5) {
            mainTank -= 5;
            if (additionalTank > 0) {
                mainTank += 1;
                additionalTank--;
            }
            distance += 50;
        }
        distance += mainTank * 10;
        return distance;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(mainTank) — Linear to how many sets of 5 liters you can consume. Bounded, practically negligible at n ≤ 100.
- **Space Complexity:** O(1) — Constant space usage.

---

## 🌟 Critical Review

Let’s strip it down:

- **Positive:**  
  Very clean, simple while-loop solution. Pragmatic enough for the problem's hard limits (mainTank ≤ 100). No unnecessary object creation, no method chaining mess.

- **Skeptical Reality:**  
  Your while-loop is efficient here, but the broader flaw is **conceptual rigidity**.  
  If tomorrow the business rule changes to "transfer after 4 liters" or "transfer 2 liters at a time," your code would **not adapt** easily.  
  **Hard-coded 5** is a liability. Always parameterize business rules unless you *know* requirements are cast in stone — and even then, they rarely are.

- **Maintenance Risk:**  
  No clear separation of concerns: fuel usage logic and distance tracking are tightly coupled. In real-world enterprise systems (think logistics or automotive software), you would modularize this — e.g., have a `consumeFuel` method and a `transferFuel` method.  

---

## 📢 Final Verdict
- **Working?** ✅
- **Production-Ready for Critical Systems?** ⚠️ (Parameterization issues)
- **Would a Code Reviewer Flag This?** Yes, with a note saying, "good for now, refactor later."

---

> ✅ **Recommendation:** Always think about scalability of rules, even if the given limits suggest "hack it fast." Senior engineers get promoted for protecting code from future volatility — not just solving for the current sprint.
