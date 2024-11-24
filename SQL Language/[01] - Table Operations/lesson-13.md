## 📝 **SQL Lesson 13: Inserting Rows**

This lesson covers how to insert new data into a database using the `INSERT` statement. It also highlights how schemas define the structure of data in tables, ensuring consistency and efficiency.

---

### **What is a Schema?**

A **schema** defines the structure of a database, including the tables, columns, and data types. For example, in the **Movies** table, the column `year` will store integers, and `title` will store strings. This fixed structure helps manage large datasets.

---

### **Inserting Data into a Table**

The `INSERT` statement allows us to insert one or more rows of data into a table.

#### **Insert Statement with Values for All Columns:**

```sql
INSERT INTO mytable
VALUES (value1, value2, ...),
       (value1_2, value2_2, ...);
```

#### **Insert Statement with Specific Columns:**

If you don’t want to insert data into every column, specify only the columns you want to populate:

```sql
INSERT INTO mytable (column1, column2, ...)
VALUES (value1, value2, ...);
```

#### **Insert Statement with Expressions:**

You can also use expressions, such as mathematical operations or string formatting, when inserting data:

```sql
INSERT INTO boxoffice (movie_id, rating, sales_in_millions)
VALUES (1, 9.9, 283742034 / 1000000);
```

---

## 🏢 **Movies and Box Office Tables**

Here’s the current structure for the **Movies** and **BoxOffice** tables:

### **Movies Table**

| **id** | **title**    | **director**  | **year** | **length_minutes** |
| ------ | ------------ | ------------- | -------- | ------------------ |
| 1      | Toy Story    | John Lasseter | 1995     | 81                 |
| 2      | A Bug's Life | John Lasseter | 1998     | 95                 |
| 3      | Toy Story 2  | John Lasseter | 1999     | 93                 |

### **BoxOffice Table**

| **movie_id** | **rating** | **domestic_sales** | **international_sales** |
| ------------ | ---------- | ------------------ | ----------------------- |
| 3            | 7.9        | 245852179          | 239163000               |
| 1            | 8.3        | 191796233          | 170162503               |
| 2            | 7.2        | 162798565          | 200600000               |

---

## 📝 **Exercise 13 — Tasks**

### 1️⃣ **Add Toy Story 4 to the Movies Table**

To add **Toy Story 4** to the Movies table, since the `id` is auto-incrementing, we can insert the `title`, `director`, `year`, and `length_minutes` columns:

```sql
INSERT INTO movies (title, director, year, length_minutes)
VALUES ('Toy Story 4', 'Josh Cooley', 2019, 100);
```

This query adds a new row with **Toy Story 4** directed by **Josh Cooley** in **2019** with a length of **100 minutes**.

### 2️⃣ **Add the BoxOffice Information for Toy Story 4**

To insert the box office data, you need to insert the movie's **rating**, **domestic sales**, and **international sales** into the **BoxOffice** table. The `movie_id` for Toy Story 4 will be the next available ID, which is `4`:

```sql
INSERT INTO boxoffice (movie_id, rating, domestic_sales, international_sales)
VALUES (4, 8.7, 340000000, 270000000);
```

This query inserts the box office data for **Toy Story 4**, which had a **rating** of **8.7**, **domestic sales** of **340 million**, and **international sales** of **270 million**.

---

## 📚 **Conclusion**

- The `INSERT` statement is essential for adding new data into a database.
- You can insert data into specific columns, and even use expressions when inserting values.
- The **Movies** and **BoxOffice** tables are linked by the `movie_id`, which ties the movie details with the box office data.

Keep practicing with `INSERT` statements and exploring more ways to manipulate data!
