# 📝 **SQL Lesson 8: A short note on NULLs**

In this lesson, we will learn about **NULL values** in SQL and how to handle them in queries. A **NULL** value is used to represent missing, undefined, or unknown data in a database. It's crucial to handle NULL values carefully because they can affect query results and behavior.

---

## 🔍 **Why Avoid NULLs?**

While it's sometimes necessary to have **NULL values** in a database (for cases like incomplete data), it's often better to use default values, such as:

- `0` for numeric columns
- Empty strings (`""`) for text columns

### **Handling NULLs in Queries**

To filter or check for NULL values, you use the `IS NULL` or `IS NOT NULL` constraints in your query.

---

### **Query Syntax for NULL Constraints:**

```sql
SELECT column, another_column, …
FROM mytable
WHERE column IS/IS NOT NULL
AND/OR another_condition;
```

- **`IS NULL`**: Tests whether a column value is NULL.
- **`IS NOT NULL`**: Tests whether a column value is not NULL.

---

## 🏢 **Employee and Building Tables Review**

We’ll continue using the **buildings** and **employees** tables from the previous lesson, but now we've added employees who haven't been assigned to any building yet.

### **Buildings Table**

| **building_name** | **capacity** |
| ----------------- | ------------ |
| 1e                | 24           |
| 1w                | 32           |
| 2e                | 16           |
| 2w                | 20           |

### **Employees Table**

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
| Engineer | Yancy I.   | NULL         | 0                  |
| Artist   | Oliver P.  | NULL         | 0                  |

---

## 📝 **Exercise 8 — Tasks**

### 1️⃣ **Find the name and role of all employees who have not been assigned to a building**

This query finds employees who have a **NULL** value in the `building` column, meaning they have not been assigned to a building yet:

```sql
SELECT name, role
FROM employees
WHERE building IS NULL;
```

---

### 2️⃣ **Find the names of the buildings that hold no employees**

This query checks the **buildings** table to find buildings that do not have any employees assigned to them. We do this by using a **LEFT JOIN** between the `buildings` and `employees` tables, filtering for rows where the `building` in `employees` is **NULL**:

```sql
SELECT b.building_name
FROM buildings b
LEFT JOIN employees e ON b.building_name = e.building
WHERE e.building IS NULL;
```

---

## 📚 **Next Steps**

Now that you have a good grasp of how to handle **NULL values**, the next lesson will help you master more advanced SQL concepts like **aggregation** and **grouping**. Keep practicing with various queries and experiment with handling NULLs in different scenarios! 🚀

---
