# 🔗 **SQL Lesson 6: Multi-table Queries with JOINs**

In this lesson, we will learn how to combine data from multiple tables using **JOINs**. In the real world, database normalization is used to split data into different tables, which can be joined together to retrieve comprehensive results.

---

## 🔍 **Multi-table Queries with INNER JOIN**

To combine data from multiple tables, SQL uses the **JOIN** clause. Specifically, the **INNER JOIN** retrieves data where matching values exist in both tables based on a shared key.

### **Basic INNER JOIN Syntax**

```sql
SELECT column, another_table_column, …
FROM mytable
INNER JOIN another_table
    ON mytable.id = another_table.id
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

This query matches rows from two tables (based on the key) and combines them into a single result. After the **INNER JOIN**, other query clauses like **WHERE**, **ORDER BY**, and **LIMIT** are applied.

---

## 🎬 **Pixar Movies & BoxOffice Tables**

For practice, we have two tables:

### **Movies Table**

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

### **BoxOffice Table**

| **movie_id** | **rating** | **domestic_sales** | **international_sales** |
| ------------ | ---------- | ------------------ | ----------------------- |
| 5            | 8.2        | 380843261          | 555900000               |
| 14           | 7.4        | 268492764          | 475066843               |
| 8            | 8          | 206445654          | 417277164               |
| 12           | 6.4        | 191452396          | 368400000               |
| 3            | 7.9        | 245852179          | 239163000               |
| 6            | 8          | 261441092          | 370001000               |
| 9            | 8.5        | 223808164          | 297503696               |
| 11           | 8.4        | 415004880          | 648167031               |
| 1            | 8.3        | 191796233          | 170162503               |
| 7            | 7.2        | 244082982          | 217900167               |
| 10           | 8.3        | 293004164          | 438338580               |
| 4            | 8.1        | 289916256          | 272900000               |
| 2            | 7.2        | 162798565          | 200600000               |
| 13           | 7.2        | 237283207          | 301700000               |

---

## 📝 **Exercise 6 — Tasks**

Using the **INNER JOIN** clause, solve the following tasks:

---

### 1️⃣ **Find the domestic and international sales for each movie**

```sql
SELECT m.title, b.domestic_sales, b.international_sales
FROM movies m
INNER JOIN boxoffice b ON m.id = b.movie_id;
```

---

### 2️⃣ **Show the sales numbers for each movie that did better internationally rather than domestically**

```sql
SELECT m.title, b.domestic_sales, b.international_sales
FROM movies m
INNER JOIN boxoffice b ON m.id = b.movie_id
WHERE b.international_sales > b.domestic_sales;
```

---

### 3️⃣ **List all the movies by their ratings in descending order**

```sql
SELECT m.title, b.rating
FROM movies m
INNER JOIN boxoffice b ON m.id = b.movie_id
ORDER BY b.rating DESC;
```

---

## 📚 **Next Steps**

You’ve now learned how to work with **multi-table queries** using **INNER JOINs**! These are crucial when working with normalized databases. Practice more by adding more complex conditions or joining additional tables. In the next lesson, you’ll learn about more advanced types of JOINs! 🚀

---
