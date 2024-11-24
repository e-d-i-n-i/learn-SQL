## 📝 **SQL Lesson 15: Deleting Rows**

In SQL, you can delete rows from a table using the `DELETE` statement. It's crucial to use the `WHERE` clause to specify which rows you want to remove. If you omit the `WHERE` clause, **all rows** will be deleted.

---

### **Delete Statement with Condition:**

```sql
DELETE FROM mytable
WHERE condition;
```

- **`WHERE` clause**: Determines which rows to delete based on a condition.
- If you leave out the `WHERE` clause, **all rows** are deleted, so **be extra cautious**.

---

### **Taking Extra Care**

Before running a `DELETE` statement, it's a good practice to test the condition using a `SELECT` query to ensure you’re deleting the correct rows. Always double-check your `DELETE` queries, especially in production environments, as this action is **irreversible** without a backup.

---

## 🏢 **Movies Table (Before Deletion)**

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

## 📝 **Exercise 15 — Tasks**

### 1️⃣ **Remove all Movies Released Before 2005**

To remove all movies that were released **before 2005**:

```sql
DELETE FROM movies
WHERE year < 2005;
```

### 2️⃣ **Remove all Movies Directed by Andrew Stanton**

Since **Andrew Stanton** has left the studio, remove all movies directed by him:

```sql
DELETE FROM movies
WHERE director = 'Andrew Stanton';
```

---

## 📚 **Conclusion**

The `DELETE` statement allows you to remove data from a table, but always ensure you're deleting the right rows by verifying your conditions first. Running a `SELECT` query with the same `WHERE` clause can help you double-check which rows will be affected.
