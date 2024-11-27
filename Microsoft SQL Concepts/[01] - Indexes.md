# **What Are Indexes?**

## **Definition**

An **index** in SQL is a data structure that improves the speed of data retrieval operations on a database table. It functions like an index in a book, allowing you to locate specific rows in a table without scanning every row.

---

## **Types of Indexes**

1. **Clustered Index**:

   - Sorts and stores the data rows in the table based on the key values.
   - A table can only have one clustered index.
   - Example: Think of a phone book where names are stored alphabetically.

2. **Non-clustered Index**:
   - Contains a pointer to the actual data in the table.
   - A table can have multiple non-clustered indexes.
   - Example: Think of an index at the back of a book with page references.

---

## **How Indexes Work**

- When a query is executed, the database engine checks if there’s an index on the column used in the query's `WHERE` clause.
- If an index exists, the engine uses it to find the relevant rows faster than scanning the entire table.

---

## **Creating Indexes**

### **Clustered Index Example**

```sql
-- Creating a clustered index on the primary key
CREATE CLUSTERED INDEX idx_emp_id ON Employees (EmployeeID);

-- Query that benefits from the index
SELECT *
FROM Employees
WHERE EmployeeID = 101;
```

### **Non-clustered Index Example**

```sql
-- Creating a non-clustered index on the LastName column
CREATE NONCLUSTERED INDEX idx_lastname ON Employees (LastName);

-- Query that benefits from the index
SELECT *
FROM Employees
WHERE LastName = 'Smith';
```

---

## **Advantages of Indexes**

1. **Faster Query Performance**: Speeds up search operations by narrowing down the data range.
2. **Efficient Sorting**: Helps with `ORDER BY` and `GROUP BY` clauses.
3. **Primary Key Enforcement**: Automatically creates a clustered index.

---

## **Disadvantages of Indexes**

1. **Slower Inserts, Updates, and Deletes**:
   - The index must be updated every time the data is modified.
2. **Storage Overhead**:
   - Indexes consume additional disk space.

---

## **Dropping an Index**

```sql
-- Dropping an index
DROP INDEX idx_lastname ON Employees;
```

---

## **Practice Example**

### Scenario:

You manage an **Employees** table with columns `EmployeeID`, `FirstName`, `LastName`, and `Department`.

**Task:**

1. Create a clustered index on `EmployeeID`.
2. Create a non-clustered index on `Department`.
3. Query to retrieve employees in the "HR" department.

### Solution:

```sql
-- Clustered Index
CREATE CLUSTERED INDEX idx_emp_id ON Employees (EmployeeID);

-- Non-clustered Index
CREATE NONCLUSTERED INDEX idx_department ON Employees (Department);

-- Query using the index
SELECT *
FROM Employees
WHERE Department = 'HR';
```

---
