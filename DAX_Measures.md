# DAX Measures

This file contains the main DAX measures used in the Bank Customer Churn Analysis Power BI dashboard.

---

## 1. Total Customers

```DAX
Total Customers = COUNTROWS(Bank_Churn)
```
## 2. Exited Customers

```DAX
Exited Customers =
CALCULATE(
    [Total Customers],
    Bank_Churn[Exited] = 1
)
```
## 3. Retention Rate

```DAX
Retention Rate =
DIVIDE(
    [Total Customers] - [Exited Customers],
    [Total Customers],
    0
)
```
## 4. Churn Rate

```DAX
Churn Rate =
DIVIDE(
    [Exited Customers],
    [Total Customers],
    0
)
```
## 5. Active member Rate

```DAX
Active Member Rate =
DIVIDE(
    CALCULATE(
        [Total Customers],
        Bank_Churn[IsActiveMember] = 1
    ),
    [Total Customers],
    0
)
```
## 6. Average Balance

```DAX
Avg_balance = AVERAGE(Bank_Churn[Balance])
```
## 7. Average Salary

```DAX
Avg_salary = AVERAGE(Bank_Churn[EstimatedSalary])
```
```markdown
# Calculated Columns

## Customer Age Group

```DAX
Customer Age Group =
IF(
    Bank_Churn[Age] < 30,
    "Young",
    IF(
        Bank_Churn[Age] < 50,
        "Middle",
        "Senior"
    )
)

Tenure Category =
IF(
    Bank_Churn[Tenure] <= 5,
    "Short Tenure",
    "Long Tenure"
)

Balance Status =
IF(
    Bank_Churn[Balance] = 0,
    "Zero Balance",
    "Has Balance"
)

