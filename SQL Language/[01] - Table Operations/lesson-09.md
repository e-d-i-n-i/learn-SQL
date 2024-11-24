# 📝 **SQL Lesson 9: Queries with Expressions**

In this lesson, we’ll learn how to use **expressions** in SQL queries to perform calculations, transformations, and logic on column values. Expressions can use arithmetic, string functions, and other database-specific functions to process the data directly in the query.

## 🔍 **What are Expressions?**

Expressions in SQL allow us to perform computations or transformations on column values while retrieving the data. For example, we can combine columns, apply mathematical operations, or format text, all within a query.

### **Example Query with Expressions:**

```sql
SELECT particle_speed / 2.0 AS half_particle_speed
FROM physics_data
WHERE ABS(particle_position) * 10.0 > 500;
```

In this example:

- **`particle_speed / 2.0`** is an expression that calculates half the speed.
- **`ABS(particle_position) * 10.0 > 500`** is another expression that transforms the particle position.

### **Alias for Expressions:**

When you use expressions, it’s good practice to give them descriptive aliases using the `AS` keyword. This makes the result easier to understand.

```sql
SELECT col_expression AS expr_description, …
FROM mytable;
```

---

## 🏢 **Movie and BoxOffice Tables Review**

In this exercise, we will be working with two tables:

1. **movies** table – contains data about movie titles, directors, release years, and movie lengths.
2. **boxoffice** table – contains box office ratings and sales data.

### **Movies Table:**

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

### **BoxOffice Table:**

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

## 📝 **Exercise 9 — Tasks**

### 1️⃣ **List all movies and their combined sales in millions of dollars**

We can sum the **domestic_sales** and **international_sales** for each movie, convert them into millions by dividing by 1,000,000, and display the result as `combined_sales`. This query uses an expression for the combined sales:

```sql
SELECT m.title,
       (b.domestic_sales + b.international_sales) / 1000000 AS combined_sales_million
FROM movies m
JOIN boxoffice b ON m.id = b.movie_id;
```

---

### 2️⃣ **List all movies and their ratings in percent**

To display ratings as percentages, multiply the rating by 10. Here's the query:

```sql
SELECT m.title,
       b.rating * 10 AS rating_percent
FROM movies m
JOIN boxoffice b ON m.id = b.movie_id;
```

---

### 3️⃣ **List all movies that were released in even-numbered years**

We can filter the **movies** based on the **year** column to select only the even-numbered years:

```sql
SELECT title, year
FROM movies
WHERE year % 2 = 0;
```

---

## 📚 **Next Steps**

By using expressions, you can make your queries more powerful and flexible, performing real-time calculations directly within SQL. Practice these techniques with different functions and complex queries to become more comfortable with their usage!
