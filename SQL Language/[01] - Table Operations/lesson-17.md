## 📝 **SQL Lesson 17: Altering Tables**

As your database evolves, you may need to modify the structure of your tables. The `ALTER TABLE` statement allows you to:

- **Add new columns** to a table.
- **Remove columns** (in some databases).
- **Rename tables**.
- **Make other changes** depending on the database system used.

---

### **Add Columns:**

To add a new column to an existing table, use the `ALTER TABLE` statement with `ADD`:

```sql
ALTER TABLE mytable
ADD column DataType OptionalTableConstraint DEFAULT default_value;
```

- **`column`**: The name of the new column.
- **`DataType`**: The data type for the column (e.g., `FLOAT`, `TEXT`).
- **Optional constraints**: Any constraints for the new column (e.g., `NOT NULL`, `DEFAULT`).

### **Remove Columns:**

To remove a column, you use `DROP`. However, not all databases support this feature (e.g., SQLite does not). In such cases, you may need to recreate the table and migrate the data.

```sql
ALTER TABLE mytable
DROP column_to_be_deleted;
```

### **Rename Table:**

You can rename a table using the `RENAME TO` clause:

```sql
ALTER TABLE mytable
RENAME TO new_table_name;
```

### **Other Changes:**

Different database systems (e.g., MySQL, PostgreSQL, SQLite, Microsoft SQL Server) may support various additional features, so always refer to the documentation for your specific database.

---

## 📝 **Exercise 17 — Tasks**

Given the **Movies** table:

| id  | title               | director       | year | length_minutes |
| --- | ------------------- | -------------- | ---- | -------------- |
| 1   | Toy Story           | John Lasseter  | 1995 | 81             |
| 2   | A Bug's Life        | John Lasseter  | 1998 | 95             |
| 3   | Toy Story 2         | John Lasseter  | 1999 | 93             |
| 4   | Monsters, Inc.      | Pete Docter    | 2001 | 92             |
| 5   | Finding Nemo        | Andrew Stanton | 2003 | 107            |
| 6   | The Incredibles     | Brad Bird      | 2004 | 116            |
| 7   | Cars                | John Lasseter  | 2006 | 117            |
| 8   | Ratatouille         | Brad Bird      | 2007 | 115            |
| 9   | WALL-E              | Andrew Stanton | 2008 | 104            |
| 10  | Up                  | Pete Docter    | 2009 | 101            |
| 11  | Toy Story 3         | Lee Unkrich    | 2010 | 103            |
| 12  | Cars 2              | John Lasseter  | 2011 | 120            |
| 13  | Brave               | Brenda Chapman | 2012 | 102            |
| 14  | Monsters University | Dan Scanlon    | 2013 | 110            |

### **Task 1: Add Aspect_ratio Column**

To add a column `Aspect_ratio` with a `FLOAT` data type, we can use:

```sql
ALTER TABLE movies
ADD Aspect_ratio FLOAT;
```

### **Task 2: Add Language Column**

To add a column `Language` with a `TEXT` data type and set the default value to `"English"`, use:

```sql
ALTER TABLE movies
ADD Language TEXT DEFAULT 'English';
```

---

These `ALTER TABLE` statements will add the `Aspect_ratio` and `Language` columns to the existing `movies` table.
