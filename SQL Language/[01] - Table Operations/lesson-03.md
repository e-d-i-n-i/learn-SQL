# 🎬 **SQL Lesson 3: Queries with Constraints (Pt. 2)**

Learn how to filter text data using powerful string comparison operators, including pattern matching with `LIKE`, and how to handle lists with `IN` and `NOT IN`.

---

## 📚 **Text Operators for WHERE Clauses**

| **Operator** | **Condition**                        | **Example**                  |
| ------------ | ------------------------------------ | ---------------------------- |
| `=`          | Case-sensitive exact match           | `col_name = "abc"`           |
| `!=` or `<>` | Case-sensitive inequality            | `col_name != "abcd"`         |
| `LIKE`       | Case-insensitive match               | `col_name LIKE "ABC"`        |
| `NOT LIKE`   | Case-insensitive inequality          | `col_name NOT LIKE "ABCD"`   |
| `%`          | Wildcard for zero or more characters | `col_name LIKE "%AT%"`       |
| `_`          | Wildcard for a single character      | `col_name LIKE "AN_"`        |
| `IN (…)`     | Value exists in a list               | `col_name IN ("A", "B")`     |
| `NOT IN (…)` | Value does not exist in a list       | `col_name NOT IN ("X", "Y")` |

---

## 🌟 **Movies Table Example**

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
| 87     | WALL-G              | Brenda Chapman | 2042     | 97                 |

---

## 🧑‍💻 **Exercise 3 — Tasks**

1️⃣ **Find all the Toy Story movies**

```sql
SELECT *
FROM movies
WHERE title LIKE "Toy Story%";
```

2️⃣ **Find all the movies directed by John Lasseter**

```sql
SELECT *
FROM movies
WHERE director = "John Lasseter";
```

3️⃣ **Find all the movies (and director) not directed by John Lasseter**

```sql
SELECT title, director
FROM movies
WHERE director != "John Lasseter";
```

4️⃣ **Find all the WALL-\* movies**

```sql
SELECT *
FROM movies
WHERE title LIKE "WALL-%";
```
