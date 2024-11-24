## 📝 **SQL Lesson 18: Dropping Tables**

Sometimes, you may want to completely remove a table, along with all of its data and schema. You can do this using the `DROP TABLE` statement.

### **Drop Table Statement:**

To drop a table, the basic syntax is:

```sql
DROP TABLE IF EXISTS mytable;
```

- **`IF EXISTS`**: This optional clause ensures that no error is thrown if the specified table does not exist.

When you drop a table, **all** the data, constraints, and the table schema will be removed from the database. If other tables are dependent on it (e.g., through foreign keys), you must handle those dependencies first, either by deleting them or altering them to remove the dependencies.

---

## 📝 **Exercise 18 — Tasks**

To clean up and remove the **Movies** table and the **BoxOffice** table:

```sql
DROP TABLE IF EXISTS movies;
DROP TABLE IF EXISTS BoxOffice;
```

These statements will completely remove both the **Movies** and **BoxOffice** tables if they exist, along with all their data and structure.
