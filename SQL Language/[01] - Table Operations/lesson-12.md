## 📝 **SQL Lesson 12: Order of Execution of a Query**

This lesson focuses on the order in which SQL query clauses are executed. Understanding the sequence is important to correctly interpret the results and to avoid errors when constructing complex queries.

---

### **Query Order of Execution:**

1. **FROM and JOINs**
   - The first step, where SQL begins by gathering the necessary data, including any tables joined together.
2. **WHERE**
   - Filters rows based on conditions before the grouping takes place.
3. **GROUP BY**
   - Groups rows based on the specified column(s).
4. **HAVING**
   - Filters the results after the `GROUP BY` step, allowing constraints on grouped rows.
5. **SELECT**
   - Computes the expressions in the `SELECT` clause.
6. **DISTINCT**
   - Removes duplicates from the result set based on the specified columns.
7. **ORDER BY**
   - Sorts the result set by specified column(s) in ascending or descending order.
8. **LIMIT / OFFSET**
   - Restricts the number of rows returned by the query, applying pagination if needed.

---

## 🏢 **Movies and Box Office Tables**

Here are the **movies** and **boxoffice** tables, which we'll use for the exercise:

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

### **Box Office Table**

| **movie_id** | **rating** | **domestic_sales** | **international_sales** |
| ------------ | ---------- | ------------------ | ----------------------- |
| 5            | 8.2        | 380843261          | 555900000               |
| 14           | 7.4        | 268492764          | 475066843               |
| 8            | 8.0        | 206445654          | 417277164               |
| 12           | 6.4        | 191452396          | 368400000               |
| 3            | 7.9        | 245852179          | 239163000               |
| 6            | 8.0        | 261441092          | 370001000               |
| 9            | 8.5        | 223808164          | 297503696               |
| 11           | 8.4        | 415004880          | 648167031               |
| 1            | 8.3        | 191796233          | 170162503               |
| 7            | 7.2        | 244082982          | 217900167               |
| 10           | 8.3        | 293004164          | 438338580               |
| 4            | 8.1        | 289916256          | 272900000               |
| 2            | 7.2        | 162798565          | 200600000               |
| 13           | 7.2        | 237283207          | 301700000               |

---

## 📝 **Exercise 12 — Tasks**

### 1️⃣ **Find the number of movies each director has directed**

To count the number of movies directed by each director, you need to use the `COUNT()` function with `GROUP BY` for the **director** column:

```sql
SELECT director, COUNT(*) AS number_of_movies_directed
FROM movies
GROUP BY director;
```

---

### 2️⃣ **Find the total domestic and international sales that can be attributed to each director**

To calculate the total **domestic** and **international** sales for each director, use the `SUM()` function with `GROUP BY` for the **director** column:

```sql
SELECT director,
       SUM(domestic_sales) AS total_domestic_sales,
       SUM(international_sales) AS total_international_sales
FROM movies
JOIN boxoffice ON movies.id = boxoffice.movie_id
GROUP BY director;
```

---

## 📚 **Conclusion**

- **ORDER OF EXECUTION**: Understanding the execution order in SQL queries is key to constructing accurate and efficient queries.
- **GROUP BY** and **HAVING** are useful when working with aggregate functions, allowing you to group data and filter results.
- **JOINs** and **WHERE** filter and combine data from multiple tables to get richer results.

Keep practicing with different queries to get more comfortable with these concepts!
