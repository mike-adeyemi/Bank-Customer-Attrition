# HR-Dashboard-Excel-Power BI

![HR-Dashboard](https://github.com/user-attachments/assets/f9017065-3fb9-4c58-a3b8-410681868ee2)

## Data Used

**Data** - HR Data with **10,000 rows** of Bank Customer Attrition data

**Data Cleaning & Analysis** - Excel 

**Data Visulaization** - Power BI

[Datasets](https://github.com/assets/datasets/Bank-Customer-Attrition-Insights-Data.xlsx)

## Questions
1. What is the customer breakdown by Card Type?
2. What is the card type breakdown by percentage rate of total revenue?
3. What is the salary breakdown by age?
4. What is the card type breakdown by salary?
5. Whaqt is the score card breakdown by Age?
6. What is the percentage rate of customer that complaint and not complaint?

## Summary of Findings

### 1. Customer breakdown by Card Type

|Gender|Customer with Credit Card|Customer without Credit Card|
|-|-|-|
|Male|3,900|1,600|
|Female|3,200|1,400|


**Insights:**
- The majority of customers own a credit card, with **7,100 out of 10,000 customers** having one.
- There are more **male customers with credit cards (3.9K)** than female customers (3.2K).
- Similarly, more **males (1.6K)** than **females (1.4K)** do not own a credit card.
- This suggests that males are more likely to use credit cards, which may indicate different spending behaviors between genders.


### 2. Card Type Breakdown by Percentage of Total Revenue

|Card Type|Percentage Revenue (%)|
|-|-|
|DIAMOND|25.93%|
|GOLD|25.09|
|PLATINUM|24.69|
|SILVER|24.29%|

**Insights:**
- The **DIAMOND card type** contributes the highest share of total revenue (25.93%), followed by **GOLD (25.09%)** and **PLATINUM (24.69%).**
- The differences between the card types in terms of revenue contribution are minimal, with only a **1.64% gap** between the **highest (DIAMOND)** and the **lowest (SILVER)**.
- This indicates that all card types are performing relatively evenly in terms of revenue, though DIAMOND is leading.


### 3. Salary breakdown by age

|Age Group|Salary($)|
|-|-|
|18-24|47,165.18|
|25-34|322,471.05|
|35-44|396,054.18|
|45-54|150,878.20|
|55-64|56,029.49|
|65+|28,304.30|

**Insights:**
- The highest-earning age group is **35-44 years** with an average salary of **$396,054.18.**
- Younger customers (18-24) earn significantly less **($47,165.18)** compared to older age groups.
- Salaries peak between **35-44,** then drop sharply in **45-54,** and decline further for customers aged 55 and above.
- This suggests that middle-aged customers are the most financially stable and likely to engage in higher banking activities.
  

### 4. Card type breakdown by salary


|Card Type|Customer Salary ($)|
|-|-|
|SILVER|252,326,935|
|GOLD|251,578,501|
|PLATINUM|249,992,874|
|DIAMOND|247,004089|


**Insights:**
- The **SILVER cardholders** have the highest combined salary **($252M)**, followed by **GOLD ($251M)** and **PLATINUM ($249M).**
- The **DIAMOND card type**, which has the highest revenue percentage, surprisingly has the lowest combined salary.
- This suggests that revenue generation is **not solely dependent on income level** but also on spending behavior.


### 5. What is the score card breakdown by Age

|Age Group|Credit Score|
|-|-|
|18-24|457|
|25-34|3,222|
|35-44|3,981|
|45-54|1,458|
|55-64|600|
|65+|282|

**Insights:**
- Customers aged **35-44** have the highest **credit score (3,981)**, aligning with their peak income levels.
- Younger customers **(18-24)** and older customers **(65+)** have the lowest credit scores, likely due to limited credit history or financial constraints.
- The sharp decline in credit scores for customers **45+ years** suggests they may rely less on credit or face difficulties in maintaining good credit standing.

### 6. Complaint Rate by Gender

|Gender|Complaint Customer|Customer without Complaint |
|-|-|-|
|Male|16.53%|83.47%|
|Female|25.14%|74.86%|



**Insights:**
- 25.14% of female customers have filed complaints, compared to 16.53% of male customers.
- This suggests that female customers may be experiencing more service issues, dissatisfaction, or unmet expectations.
- However, the majority of customers (both genders) do not file complaints, with more than 74% satisfaction levels.

# DAX Measure

### Active
```sql
    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[IsActiveMember] = 1
    )
```

### Active Member Percentage
```sql
    DIVIDE(
        [Active], 
        COUNTROWS(HR_Banking_Analytics), 
        0
    )
```

### Attribute

```sql

    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[IsActiveMember] = 0
    )
```

### Average Credit Score

```sql
AVERAGE(HR_Banking_Analytics[CreditScore])
```

### Avg Salary

```sql
var a = CALCULATE(AVERAGE(HR_Banking_Analytics[EstimatedSalary]))
RETURN a
````

### Complain Customer

```sql
    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[Complain] = 1
    )
```

### Customer with CreditCard 

```sql
    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[HasCrCard] = 1
    )
```

### Customer without Credit Card

```sql
    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[HasCrCard] = 0
    )
```

### Headcount 

```sql
DISTINCTCOUNT(HR_Banking_Analytics[CustomerId])
```

### Not Complain Customer
```sql
    CALCULATE(
        COUNTROWS(HR_Banking_Analytics), 
        HR_Banking_Analytics[Complain] = 0
    )
```

### Total Balance

```sql
SUM(HR_Banking_Analytics[Balance])
```

### Total Customer Salary
```sql
SUM(HR_Banking_Analytics[EstimatedSalary])
```
### Total Point Earned 

```sql
sum(HR_Banking_Analytics[Point Earned])
```
## **Recommendations**
- **Expand Credit Card Usage:** More targeted strategies should encourage female customers to adopt credit cards.
- **Revenue Maximization:** Consider incentives to increase spending in lower-revenue card tiers (SILVER, PLATINUM).
- **Age-Based Financial Strategies:** Offer financial products tailored to different age groups based on salary trends.
- **Credit Education & Support:** Introduce credit-building programs, especially for younger and older customers.
- **Customer Satisfaction Improvement:** Address service complaints, particularly among female customers, to enhance retention and loyalty.

