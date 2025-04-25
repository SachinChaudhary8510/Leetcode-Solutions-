# 🚀 LeetCode Problem 3280: Convert Date to Binary

## 📘 Problem Statement
You are given a string `date` representing a Gregorian calendar date in the `yyyy-mm-dd` format.

You need to convert:
- The **year**, **month**, and **day** into their **binary representation** (without leading zeroes),
- And return a single string in the form: `year-binary-month-binary-day-binary`.

---

## 🔍 Examples

### Example 1:
**Input:**  
`date = "2080-02-29"`  
**Output:**  
`100000100000-10-11101`  
**Explanation:**  
Year = 2080 → `100000100000`  
Month = 2 → `10`  
Day = 29 → `11101`

---

### Example 2:
**Input:**  
`date = "1900-01-01"`  
**Output:**  
`11101101100-1-1`  
**Explanation:**  
Year = 1900 → `11101101100`  
Month = 1 → `1`  
Day = 1 → `1`

---

## 🔒 Constraints
- `date.length == 10`
- `date[4] == date[7] == '-'` and all other `date[i]` are digits.
- The date is valid and falls between **Jan 1, 1900** and **Dec 31, 2100** inclusive.

---

## 💻 Java Solution
```java
class Solution {
    public String convertDateToBinary(String date) {
        String str = "";

        int d = (int) (date.charAt(8) - '0') * 10 + (int) (date.charAt(9) - '0');
        String dayBinary = "";
        while (d > 0) {
            dayBinary = (d % 2) + dayBinary;
            d /= 2;
        }
        str = "-" + dayBinary;

        int month = (int) (date.charAt(5) - '0') * 10 + (int) (date.charAt(6) - '0');
        String monthBinary = "";
        while (month > 0) {
            monthBinary = (month % 2) + monthBinary;
            month /= 2;
        }
        str = "-" + monthBinary + str;

        int year = (int) (date.charAt(0) - '0') * 1000 +
                   (int) (date.charAt(1) - '0') * 100 +
                   (int) (date.charAt(2) - '0') * 10 +
                   (int) (date.charAt(3) - '0');
        String yearBinary = "";
        while (year > 0) {
            yearBinary = (year % 2) + yearBinary;
            year /= 2;
        }
        str = yearBinary + str;

        return str;
    }
}
```

---

## 🐍 Python Solution
```python
class Solution:
    def convertDateToBinary(self, date: str) -> str:
        year, month, day = map(int, date.split('-'))
        return f"{bin(year)[2:]}-{bin(month)[2:]}-{bin(day)[2:]}"
```

---

## 💠 C++ Solution
```cpp
class Solution {
public:
    string convertDateToBinary(string date) {
        int year = stoi(date.substr(0, 4));
        int month = stoi(date.substr(5, 2));
        int day = stoi(date.substr(8, 2));

        return toBinary(year) + "-" + toBinary(month) + "-" + toBinary(day);
    }

private:
    string toBinary(int num) {
        string res = "";
        while (num > 0) {
            res = char('0' + num % 2) + res;
            num /= 2;
        }
        return res;
    }
};
```

---

## ⏱️ Time and Space Complexity
- **Time Complexity:** O(log(year) + log(month) + log(day)) → effectively constant time
- **Space Complexity:** O(1) extra
