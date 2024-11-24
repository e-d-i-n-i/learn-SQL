# 🎓 **SQL Lesson 1: SELECT Queries 101**

Learn the basics of retrieving data from a SQL database using **SELECT** statements, the foundation of querying in SQL. This lesson introduces the syntax and concepts through examples and exercises.

---

## 🧐 **What is a Query?**

A **query** is a statement that declares:

1. **What data** you are looking for.
2. **Where** to find it in the database.
3. **How** to optionally transform it before it is returned.

---

## 🗂️ **Understanding Tables in SQL**

- **Tables** in SQL represent entities (e.g., `Dogs`).
- **Rows** represent specific instances of those entities (e.g., _a pug, a beagle_).
- **Columns** represent properties shared by all instances (e.g., _color of fur, length of tail_).

---

## 🛠️ **Writing Your First SELECT Queries**

### **1. Query Specific Columns**

To select specific columns from a table:

```sql
SELECT column1, column2, ...
FROM mytable;
```

For example:

```sql
SELECT title, director
FROM Movies;
```

The result is a subset of the table with only the requested columns.

---

### **2. Query All Columns**

To retrieve all columns:

```sql
SELECT *
FROM mytable;
```

This is a quick way to inspect a table by returning all its data.

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

## 🧑‍💻 **Exercise 1 — Tasks**

Write SQL queries to complete the following tasks:

1️⃣ **Find the title of each film**

```sql
SELECT title
FROM Movies;
```

2️⃣ **Find the director of each film**

```sql
SELECT director
FROM Movies;
```

3️⃣ **Find the title and director of each film**

```sql
SELECT title, director
FROM Movies;
```

4️⃣ **Find the title and year of each film**

```sql
SELECT title, year
FROM Movies;
```

5️⃣ **Find all the information about each film**

```sql
SELECT *
FROM Movies;
```

---

## 🏁 **Next Steps**

Once you've completed the above exercises, you're ready to move on to the next lessons. Keep practicing to master the art of querying relational databases!

---
