## 📝 **SQL Lesson 16: Creating Tables**

To store new entities and relationships in your database, you can create a table using the `CREATE TABLE` statement. This allows you to define the schema for the table, which includes the column names, data types, and optional constraints.

---

### **Create Table Statement:**

```sql
CREATE TABLE IF NOT EXISTS mytable (
    column DataType TableConstraint DEFAULT default_value,
    another_column DataType TableConstraint DEFAULT default_value,
    …
);
```

- **`IF NOT EXISTS`**: Prevents errors by only creating the table if it doesn't already exist.
- **Column Definitions**: Each column has a name, data type, and optional constraints or default values.

---

### **Common Data Types:**

- **`INTEGER`**: Stores whole numbers (e.g., age, count).
- **`BOOLEAN`**: Stores true/false values, typically as 1 or 0.
- **`FLOAT` / `DOUBLE` / `REAL`**: Stores precise fractional numbers (e.g., measurements).
- **`CHARACTER(num_chars)` / `VARCHAR(num_chars)` / `TEXT`**: Stores text data with varying lengths.
- **`DATE` / `DATETIME`**: Stores date and time values.
- **`BLOB`**: Stores binary data (e.g., images or files).

---

### **Common Table Constraints:**

- **`PRIMARY KEY`**: Ensures the column has unique values and can identify each row.
- **`AUTOINCREMENT`**: Automatically increments integer values when inserting new rows.
- **`UNIQUE`**: Ensures the column has unique values but doesn't have to be a primary key.
- **`NOT NULL`**: Prevents `NULL` values in a column.
- **`CHECK`**: Enforces a condition (e.g., values must be positive).
- **`FOREIGN KEY`**: Ensures data integrity by referencing another table's column.

---

### **Example Table Creation:**

To create the **Movies** table, we use the following SQL statement:

```sql
CREATE TABLE movies (
    id INTEGER PRIMARY KEY,
    title TEXT,
    director TEXT,
    year INTEGER,
    length_minutes INTEGER
);
```

This creates a table with five columns: `id`, `title`, `director`, `year`, and `length_minutes`.

---

## 📝 **Exercise 16 — Tasks**

Create a table named `Database` with the following columns:

- **Name**: A string (text) describing the name of the database.
- **Version**: A floating-point number representing the latest version of this database.
- **Download_count**: An integer count of the number of times the database was downloaded.

Since no constraints are specified, we won't include any in the table.

```sql
CREATE TABLE Database (
    Name TEXT,
    Version FLOAT,
    Download_count INTEGER
);
```

---

This SQL statement creates the `Database` table with the necessary columns, allowing you to store information about the database name, version, and download count.
