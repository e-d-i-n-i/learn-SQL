# 📝 **SQL Lesson 10: Queries with Aggregates (Pt. 1)**

In this lesson, we will explore **aggregate functions** that allow us to summarize and analyze data across multiple rows. Aggregate functions are commonly used when you want to calculate summary statistics like the total, average, or count of a dataset.

## 🔍 **What Are Aggregate Functions?**

Aggregate functions perform calculations on multiple rows of data and return a single result. These functions help us answer questions like "How many rows meet a certain condition?" or "What is the highest value in a column?"

### **Syntax of Aggregate Functions:**

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description
FROM mytable
WHERE constraint_expression;
```

### **Common Aggregate Functions:**

| **Function**                 | **Description**                                                       |
| ---------------------------- | --------------------------------------------------------------------- |
| `COUNT(*)` / `COUNT(column)` | Counts the number of rows or non-NULL values in the specified column. |
| `MIN(column)`                | Finds the smallest numerical value in the specified column.           |
| `MAX(column)`                | Finds the largest numerical value in the specified column.            |
| `AVG(column)`                | Finds the average value in the specified column.                      |
| `SUM(column)`                | Finds the sum of all numerical values in the specified column.        |

## 📊 **Grouped Aggregate Functions**

In addition to applying aggregate functions over all rows, you can use the **`GROUP BY`** clause to group rows by specific column values. For example, you can calculate the total sales per category or the average salary by department.

### **Grouped Query Syntax:**

```sql
SELECT AGG_FUNC(column_or_expression) AS aggregate_description
FROM mytable
WHERE constraint_expression
GROUP BY column;
```

The `GROUP BY` clause groups rows that share the same value in the specified column, and then the aggregate function is applied to each group.

---

## 🏢 **Employees Table Review**

Here’s the **Employees** table with data on employee roles, names, assigned buildings, and years employed:

| **role** | **name**   | **building** | **years_employed** |
| -------- | ---------- | ------------ | ------------------ |
| Engineer | Becky A.   | 1e           | 4                  |
| Engineer | Dan B.     | 1e           | 2                  |
| Engineer | Sharon F.  | 1e           | 6                  |
| Engineer | Dan M.     | 1e           | 4                  |
| Engineer | Malcom S.  | 1e           | 1                  |
| Artist   | Tylar S.   | 2w           | 2                  |
| Artist   | Sherman D. | 2w           | 8                  |
| Artist   | Jakob J.   | 2w           | 6                  |
| Artist   | Lillia A.  | 2w           | 7                  |
| Artist   | Brandon J. | 2w           | 7                  |
| Manager  | Scott K.   | 1e           | 9                  |
| Manager  | Shirlee M. | 1e           | 3                  |
| Manager  | Daria O.   | 2w           | 6                  |

---

## 📝 **Exercise 10 — Tasks**

### 1️⃣ **Find the longest time that an employee has been at the studio**

To find the employee with the longest time at the studio, use the **`MAX()`** aggregate function on the **`years_employed`** column:

```sql
SELECT MAX(years_employed) AS longest_time
FROM employees;
```

---

### 2️⃣ **For each role, find the average number of years employed by employees in that role**

To calculate the average number of years each role has been employed, use the **`AVG()`** function along with the **`GROUP BY`** clause:

```sql
SELECT role, AVG(years_employed) AS avg_years_employed
FROM employees
GROUP BY role;
```

---

### 3️⃣ **Find the total number of employee years worked in each building**

To find the total number of employee years worked for each building, use the **`SUM()`** function and group by the **`building`** column:

```sql
SELECT building, SUM(years_employed) AS total_years_worked
FROM employees
GROUP BY building;
```

---

## 📚 **Next Steps**

By using **aggregate functions**, you can easily perform summarization and analysis directly within your queries. Whether it's calculating totals, averages, or finding extreme values, these functions are a powerful tool for data analysis in SQL. Practice with different types of aggregate functions and grouping to get a deeper understanding of their capabilities.
