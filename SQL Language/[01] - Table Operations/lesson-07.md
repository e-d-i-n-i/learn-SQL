# 🔗 **SQL Lesson 7: OUTER JOINs**

In this lesson, we’ll explore **OUTER JOINs**, which allow you to include data that may not exist in both tables. Unlike the **INNER JOIN** that only retrieves rows with matching data in both tables, the **OUTER JOIN** includes rows from one or both tables, even when no matching data exists in the other table.

---

## 🔍 **LEFT, RIGHT, and FULL JOINs**

The **LEFT JOIN**, **RIGHT JOIN**, and **FULL JOIN** are used when you need to include rows from one table even if there is no matching row in the other table.

### **Basic LEFT/RIGHT/FULL JOIN Syntax**

```sql
SELECT column, another_column, …
FROM mytable
INNER/LEFT/RIGHT/FULL JOIN another_table
    ON mytable.id = another_table.matching_id
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

- **LEFT JOIN**: Includes all rows from the left table, even if there’s no matching row in the right table.
- **RIGHT JOIN**: Includes all rows from the right table, even if there’s no matching row in the left table.
- **FULL JOIN**: Includes all rows from both tables, regardless of whether a match exists in the other table.

---

## 🏢 **Employee and Building Tables**

For practice, we are working with two tables: **buildings** and **employees**.

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

---

## 📝 **Exercise 7 — Tasks**

### 1️⃣ **Find the list of all buildings that have employees**

This query retrieves the buildings that have at least one employee:

```sql
SELECT b.building_name, b.capacity
FROM buildings b
LEFT JOIN employees e ON b.building_name = e.building
WHERE e.building IS NOT NULL;
```

---

### 2️⃣ **Find the list of all buildings and their capacity**

This query lists all buildings and their capacities, including those without employees:

```sql
SELECT b.building_name, b.capacity
FROM buildings b
LEFT JOIN employees e ON b.building_name = e.building;
```

---

### 3️⃣ **List all buildings and the distinct employee roles in each building (including empty buildings)**

This query lists all buildings along with distinct roles, ensuring that even buildings without employees are included:

```sql
SELECT b.building_name, e.role
FROM buildings b
LEFT JOIN employees e ON b.building_name = e.building
GROUP BY b.building_name, e.role
ORDER BY b.building_name;
```

---

## 📚 **Next Steps**

You’ve now learned how to use **OUTER JOINs** to include rows even when there is no matching data in the other table. In the next lesson, we will explore more advanced SQL concepts such as handling **NULLs** in queries. Practice by joining additional tables and experimenting with the different JOIN types! 🚀

---
