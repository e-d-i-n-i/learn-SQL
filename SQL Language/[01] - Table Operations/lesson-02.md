# 🎓 **SQL Lesson 2: Queries with Constraints (Pt. 1)**

Learn how to filter and retrieve specific rows from large datasets using the **WHERE** clause and logical operators.

---

## 🛠️ **Using the WHERE Clause**

To filter rows, use the **WHERE** clause:

```sql
SELECT column1, column2, ...
FROM mytable
WHERE condition
    AND/OR another_condition
    AND/OR ...;
```

---

### **Useful Operators for Constraints**

| **Operator**          | **Condition**                         | **SQL Example**                 |
| --------------------- | ------------------------------------- | ------------------------------- |
| `=, !=, <, <=, >, >=` | Standard numerical operators          | `col_name != 4`                 |
| `BETWEEN … AND …`     | Value is within range (inclusive)     | `col_name BETWEEN 1 AND 10`     |
| `NOT BETWEEN … AND …` | Value is not within range (inclusive) | `col_name NOT BETWEEN 1 AND 10` |
| `IN (…)`              | Value exists in a list                | `col_name IN (2, 4, 6)`         |
| `NOT IN (…)`          | Value does not exist in a list        | `col_name NOT IN (1, 3, 5)`     |

---

## 🎥 **Movies Table Example**

| **id** | **title**           | **director**   | **year** | **length_minutes** |
| ------ | ------------------- | -------------- | -------- | ------------------ |
| 1      | Toy Story           | John Lasseter  | 1995     | 81                 |
| 2      | A Bug's Life        | John Lasseter  | 1998     | 95                 |
| 3      | Toy Story 2         | John Lasseter  | 1999     | 93                 |
| 4      | Monsters, Inc.      | Pete Docter    | 2001     | 92                 |
| 5      | Finding Nemo        | Andrew Stanton | 2003     | 107                |
| 6      | The Incredibles     | Brad Bird      | 2004     | 116                |
| 7      | Cars                | John Lasseter  | 2006     | 117                |
| 8      | Ratatouille         | Brad Bird      | 2007     | 115                |
| 9      | WALL-E              | Andrew Stanton | 2008     | 104                |
| 10     | Up                  | Pete Docter    | 2009     | 101                |
| 11     | Toy Story 3         | Lee Unkrich    | 2010     | 103                |
| 12     | Cars 2              | John Lasseter  | 2011     | 120                |
| 13     | Brave               | Brenda Chapman | 2012     | 102                |
| 14     | Monsters University | Dan Scanlon    | 2013     | 110                |

---

## 🧑‍💻 **Exercise 2 — Tasks**

1️⃣ **Find the movie with a row id of 6**

```sql
SELECT *
FROM movies
WHERE id = 6;
```

2️⃣ **Find the movies released in the years between 2000 and 2010**

```sql
SELECT *
FROM movies
WHERE year BETWEEN 2000 AND 2010;
```

3️⃣ **Find the movies not released in the years between 2000 and 2010**

```sql
SELECT *
FROM movies
WHERE year NOT BETWEEN 2000 AND 2010;
```

4️⃣ **Find the first 5 Pixar movies and their release year**

```sql
SELECT title, year
FROM movies
WHERE id <= 5;
```
