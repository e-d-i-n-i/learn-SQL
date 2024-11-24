## 📝 **SQL Lesson 14: Updating Rows**

In SQL, you can update existing data in a table using the `UPDATE` statement. This allows you to modify specific columns of one or more rows based on a condition specified in the `WHERE` clause.

---

### **Update Statement with Values:**

```sql
UPDATE mytable
SET column = value_or_expr,
    other_column = another_value_or_expr,
    …
WHERE condition;
```

- **`SET` clause**: Defines the column(s) to update and their new values (or expressions).
- **`WHERE` clause**: Ensures only rows meeting the specified condition are updated. It's crucial to avoid updating all rows by forgetting this clause.

### **Be Careful!**

Always verify your condition first by running a `SELECT` query with the same `WHERE` clause. This ensures you're updating the right rows.

---

## 🏢 **Movies Table (Before Update)**

| **id** | **title**           | **director**   | **year** | **length_minutes** |
| ------ | ------------------- | -------------- | -------- | ------------------ |
| 1      | Toy Story           | John Lasseter  | 1995     | 81                 |
| 2      | A Bug's Life        | El Directore   | 1998     | 95                 |
| 3      | Toy Story 2         | John Lasseter  | 1899     | 93                 |
| 4      | Monsters, Inc.      | Pete Docter    | 2001     | 92                 |
| 5      | Finding Nemo        | Andrew Stanton | 2003     | 107                |
| 6      | The Incredibles     | Brad Bird      | 2004     | 116                |
| 7      | Cars                | John Lasseter  | 2006     | 117                |
| 8      | Ratatouille         | Brad Bird      | 2007     | 115                |
| 9      | WALL-E              | Andrew Stanton | 2008     | 104                |
| 10     | Up                  | Pete Docter    | 2009     | 101                |
| 11     | Toy Story 8         | El Directore   | 2010     | 103                |
| 12     | Cars 2              | John Lasseter  | 2011     | 120                |
| 13     | Brave               | Brenda Chapman | 2012     | 102                |
| 14     | Monsters University | Dan Scanlon    | 2013     | 110                |

---

## 📝 **Exercise 14 — Tasks**

### 1️⃣ **Fix the Director for A Bug's Life**

The director for **A Bug's Life** is listed incorrectly as **El Directore**, but it was actually directed by **John Lasseter**. To fix this:

```sql
UPDATE movies
SET director = 'John Lasseter'
WHERE title = "A Bug's Life";
```

### 2️⃣ **Fix the Year for Toy Story 2**

The year for **Toy Story 2** is listed incorrectly as **1899**, but it was actually released in **1999**. To fix this:

```sql
UPDATE movies
SET year = 1999
WHERE title = "Toy Story 2";
```

### 3️⃣ **Fix the Title and Director for Toy Story 8**

Both the **title** and **director** for **Toy Story 8** are incorrect. The title should be **"Toy Story 3"**, and it was directed by **Lee Unkrich**. To fix this:

```sql
UPDATE movies
SET title = 'Toy Story 3', director = 'Lee Unkrich'
WHERE title = 'Toy Story 8';
```

---

## 📚 **Conclusion**

The `UPDATE` statement is powerful for modifying existing data in a database. Always test the conditions in a `SELECT` query before running the `UPDATE` to prevent unintended changes. By using `WHERE` conditions, you ensure that only the desired rows are updated.
