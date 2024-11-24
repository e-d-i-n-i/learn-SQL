# 🎯 **SQL Lesson 4: Filtering and Sorting Query Results**

This lesson focuses on techniques for filtering, sorting, and limiting query results to make data more readable and easier to analyze. You'll also learn how to handle duplicate rows and work with subsets of data effectively.

---

## 🔍 **Filtering Unique Results**

To eliminate duplicate rows in query results, SQL provides the **DISTINCT** keyword.

### **Select Query with Unique Results**

```sql
SELECT DISTINCT column, another_column, ...
FROM mytable
WHERE condition(s);
```

> **Note:** While `DISTINCT` removes duplicates across all selected columns, later lessons will cover more precise deduplication using `GROUP BY`.

---

## 📑 **Ordering Results**

SQL allows you to sort query results using the **ORDER BY** clause:

### **Select Query with Ordered Results**

```sql
SELECT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC;
```

- **ASC**: Sorts in ascending order (default).
- **DESC**: Sorts in descending order.

### **Example:** Sorting Movies Alphabetically by Title

```sql
SELECT title
FROM Movies
ORDER BY title ASC;
```

---

## 🎯 **Limiting Results**

To retrieve a subset of data, SQL provides the **LIMIT** and **OFFSET** clauses:

### **Select Query with Limited Rows**

```sql
SELECT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

- **LIMIT**: Restricts the number of rows returned.
- **OFFSET**: Skips a specified number of rows before starting to return results.

> **Did You Know?** The **LIMIT** and **OFFSET** clauses are applied after all other query clauses are executed.

---

## 🎥 **Movies Table Example**

| **id** | **title**           | **director**   | **year** | **length_minutes** |
| ------ | ------------------- | -------------- | -------- | ------------------ |
| 1      | The Incredibles     | Brad Bird      | 2004     | 116                |
| 2      | A Bug's Life        | John Lasseter  | 1998     | 95                 |
| 3      | Monsters, Inc.      | Pete Docter    | 2001     | 92                 |
| 4      | Toy Story           | John Lasseter  | 1995     | 81                 |
| 5      | WALL-E              | Andrew Stanton | 2008     | 104                |
| 6      | Finding Nemo        | Andrew Stanton | 2003     | 107                |
| 7      | Cars 2              | John Lasseter  | 2011     | 120                |
| 8      | Monsters University | Dan Scanlon    | 2013     | 110                |
| 9      | Ratatouille         | Brad Bird      | 2007     | 115                |
| 10     | Toy Story 3         | Lee Unkrich    | 2010     | 103                |
| 11     | Up                  | Pete Docter    | 2009     | 101                |
| 12     | Brave               | Brenda Chapman | 2012     | 102                |
| 13     | Toy Story 2         | John Lasseter  | 1999     | 93                 |
| 14     | Cars                | John Lasseter  | 2006     | 117                |

---

## 🧑‍💻 **Exercise 4 — Tasks**

Use the Movies table above to complete the following tasks:

1️⃣ **List all directors of Pixar movies (alphabetically), without duplicates**

```sql
SELECT DISTINCT director
FROM Movies
ORDER BY director ASC;
```

2️⃣ **List the last four Pixar movies released (ordered from most recent to least)**

```sql
SELECT title, year
FROM Movies
ORDER BY year DESC
LIMIT 4;
```

3️⃣ **List the first five Pixar movies sorted alphabetically**

```sql
SELECT title
FROM Movies
ORDER BY title ASC
LIMIT 5;
```

4️⃣ **List the next five Pixar movies sorted alphabetically**

```sql
SELECT title
FROM Movies
ORDER BY title ASC
LIMIT 5 OFFSET 5;
```

---

## 🏁 **Next Steps**

Practice using **DISTINCT**, **ORDER BY**, **LIMIT**, and **OFFSET** in different scenarios to solidify your understanding of these concepts. Ready for the next challenge? 🚀

---
