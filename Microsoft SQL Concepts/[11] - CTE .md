## **Course Title:** Advanced SQL Techniques: CTEs and Table Variables

### **Objective:**

- To understand and effectively use Common Table Expressions (CTEs) and Table Variables in SQL.
- To explore practical scenarios and benefits of using these constructs.

---

### **1. Common Table Expressions (CTEs)**

#### **1.1 What is a CTE?**

- **Definition:**  
  A CTE is a temporary result set defined within the execution scope of a `SELECT`, `INSERT`, `UPDATE`, or `DELETE` statement.

- **Characteristics:**
  - Temporary, like a subquery.
  - Improves query readability and maintainability.
  - Cannot be indexed directly.

#### **1.2 Syntax**

```sql
WITH cte_name (column1, column2, ...) AS (
    SELECT columns
    FROM tables
    WHERE condition
)
SELECT columns
FROM cte_name;
```

#### **1.3 Basic Example**

Find departments with average salaries above $60,000:

```sql
WITH DepartmentSalaries AS (
    SELECT department_id, AVG(salary) AS avg_salary
    FROM employees
    GROUP BY department_id
)
SELECT department_id, avg_salary
FROM DepartmentSalaries
WHERE avg_salary > 60000;
```

#### **1.4 Recursive CTEs**

- Used for hierarchical or recursive data processing.
- **Syntax:**

```sql
WITH RecursiveCTE (column1, column2, ...) AS (
    -- Anchor Member
    SELECT columns
    FROM table
    WHERE condition
    UNION ALL
    -- Recursive Member
    SELECT columns
    FROM table, RecursiveCTE
    WHERE condition
)
SELECT * FROM RecursiveCTE;
```

#### **1.5 Recursive Example**

Find all managers and their subordinates:

```sql
WITH EmployeeHierarchy AS (
    SELECT emp_id, manager_id, name
    FROM employees
    WHERE manager_id IS NULL -- Top-level manager
    UNION ALL
    SELECT e.emp_id, e.manager_id, e.name
    FROM employees e
    INNER JOIN EmployeeHierarchy eh ON e.manager_id = eh.emp_id
)
SELECT * FROM EmployeeHierarchy;
```

---

### **2. Table Variables**

#### **2.1 What is a Table Variable?**

- **Definition:**  
  A table variable is a special type of variable used to store temporary results in a table format. It is scoped to the batch, procedure, or function.

- **Advantages:**
  - Scoped to the session and faster for smaller datasets.
  - Ideal for temporary data manipulation.
  - Automatically cleans up when the scope ends.

#### **2.2 Syntax**

```sql
DECLARE @table_variable_name TABLE (
    column1 data_type,
    column2 data_type,
    ...
);
```

#### **2.3 Example: Basic Usage**

Store and query temporary data:

```sql
DECLARE @TempEmployees TABLE (
    emp_id INT,
    name NVARCHAR(50),
    salary DECIMAL(10, 2)
);

INSERT INTO @TempEmployees (emp_id, name, salary)
VALUES (1, 'John Doe', 75000),
       (2, 'Jane Smith', 80000);

SELECT * FROM @TempEmployees;
```

#### **2.4 Comparison with Temporary Tables**

| Feature          | Table Variables         | Temporary Tables      |
| ---------------- | ----------------------- | --------------------- |
| Scope            | Current batch/procedure | Current session       |
| Storage Location | In-memory (primarily)   | `tempdb` database     |
| Indexing         | No explicit indexes     | Can define indexes    |
| Performance      | Better for small data   | Better for large data |

---

### **3. Practical Use Cases**

#### **3.1 CTE Use Cases**

1. **Simplifying Complex Queries:**  
   Break down multi-step transformations into readable parts.

   ```sql
   WITH SalesData AS (
       SELECT product_id, SUM(quantity) AS total_sold
       FROM sales
       GROUP BY product_id
   )
   SELECT product_id, total_sold
   FROM SalesData
   WHERE total_sold > 1000;
   ```

2. **Recursive Data Processing:**  
   Generate organizational charts or file system hierarchies.

#### **3.2 Table Variable Use Cases**

1. **Temporary Data Storage:**  
   Store intermediate results for quick computations in stored procedures.

2. **Batch Processing:**  
   Use table variables to process chunks of data in a loop.

3. **Storing Output Parameters in Functions:**  
   Return temporary result sets from user-defined functions.

---

### **4. Exercises**

#### **CTE Exercises**

1. Write a query to find all employees in the same department as 'John Doe' using a CTE.
2. Use a recursive CTE to calculate the factorial of numbers up to 10.
3. Create a query with multiple CTEs to calculate department-wise total and average salaries.

#### **Table Variable Exercises**

1. Declare a table variable to store top 5 products by sales and query the results.
2. Write a stored procedure that uses a table variable to store intermediate results for generating sales reports.
3. Compare the use of a table variable vs. a temporary table for a query handling 10,000 records.
