# 📝 **SQL Lesson 11: Queries with Aggregates (Pt. 2)**

In this lesson, we expand on aggregate functions by introducing the **HAVING** clause, which allows filtering of **grouped rows**. This is crucial when you need to filter data after the grouping operation has been applied (i.e., after using `GROUP BY`).

## 🔍 **What is the HAVING Clause?**

The **`HAVING`** clause is similar to the **`WHERE`** clause, but it’s used specifically to filter rows after they have been grouped. This is particularly useful when you want to apply conditions to groups of data (e.g., sum of sales, average salary) rather than individual rows.

### **Syntax for Using the HAVING Clause:**

```sql
SELECT group_by_column, AGG_FUNC(column_expression) AS aggregate_result_alias
FROM mytable
WHERE condition
GROUP BY column
HAVING group_condition;
```

- **`WHERE`**: Filters the data before the grouping.
- **`GROUP BY`**: Groups the data based on specified column(s).
- **`HAVING`**: Filters the grouped data based on conditions applied to the aggregate results.

If you are not using **`GROUP BY`**, you don’t need **`HAVING** – just use **`WHERE`** for filtering.

---

## 🏢 **Employees Table Review**

Here’s the **Employees** table, where we will perform the exercises:

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

## 📝 **Exercise 11 — Tasks**

### 1️⃣ **Find the number of Artists in the studio (without a HAVING clause)**

To count the number of **Artists**, you can use the **`COUNT()`** function. Since we're not using **`GROUP BY`**, we don’t need the **`HAVING`** clause here.

```sql
SELECT COUNT(*) AS number_of_artists
FROM employees
WHERE role = 'Artist';
```

---

### 2️⃣ **Find the number of Employees of each role in the studio**

To count the number of employees for each role, use the **`COUNT()`** function along with **`GROUP BY`** to group by the **`role`** column:

```sql
SELECT role, COUNT(*) AS number_of_employees
FROM employees
GROUP BY role;
```

---

### 3️⃣ **Find the total number of years employed by all Engineers**

To calculate the **total number of years** worked by all Engineers, use the **`SUM()`** function and filter by the **`role`** column:

```sql
SELECT SUM(years_employed) AS total_years_employed_by_engineers
FROM employees
WHERE role = 'Engineer';
```

---

## 📚 **Next Steps**

The **`HAVING`** clause is very useful when dealing with **grouped** data and wanting to apply additional filtering after the grouping. When working with aggregate functions like **`COUNT()`**, **`SUM()`**, **`AVG()`**, and others, knowing how to properly use **`GROUP BY`** and **`HAVING`** will allow you to get deeper insights from your datasets.

Feel free to practice these queries on larger datasets for a better understanding!
