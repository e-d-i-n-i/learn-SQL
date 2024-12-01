## **Course Title:** Mastering Temporary Tables in SQL

### **Objective:**

- To understand what temporary tables are, why they are used, and how to create and manage them in SQL.
- To explore practical use cases of temporary tables.

---

### **1. Introduction to Temporary Tables**

- **Definition:**  
  Temporary tables are tables that exist temporarily during a database session and are automatically dropped when the session ends.

- **Features of Temporary Tables:**

  - Stored in the `tempdb` database.
  - Automatically deleted when the session or batch ends.
  - Visible only to the user who created them.

- **Use Cases:**
  - Storing intermediate query results.
  - Simplifying complex queries.
  - Improving query performance.

---

### **2. Types of Temporary Tables**

1. **Local Temporary Tables (`#temp_table`):**

   - Visible only within the session where they were created.
   - Dropped automatically when the session ends.

2. **Global Temporary Tables (`##temp_table`):**
   - Visible to all sessions.
   - Dropped automatically when the last session using the table ends.

---

### **3. Creating Temporary Tables**

- **Syntax:**

  ```sql
  CREATE TABLE #temp_table_name (column_name data_type, ...);
  ```

- **Example:**  
  Create a temporary table to store employee data:

  ```sql
  CREATE TABLE #temp_employees (
      emp_id INT PRIMARY KEY,
      name NVARCHAR(50),
      department NVARCHAR(50),
      salary DECIMAL(10, 2)
  );
  ```

- **Inserting Data:**
  ```sql
  INSERT INTO #temp_employees (emp_id, name, department, salary)
  VALUES (1, 'John Doe', 'IT', 75000);
  ```

---

### **4. Using Temporary Tables**

1. **Populating Temporary Tables with Query Results:**

   ```sql
   SELECT emp_id, name, department, salary
   INTO #temp_employees
   FROM employees
   WHERE department = 'IT';
   ```

2. **Querying Data from Temporary Tables:**

   ```sql
   SELECT * FROM #temp_employees;
   ```

3. **Updating Data in Temporary Tables:**
   ```sql
   UPDATE #temp_employees
   SET salary = salary * 1.10
   WHERE department = 'IT';
   ```

---

### **5. Dropping Temporary Tables**

- **Explicit Drop (Optional):**  
  Temporary tables are dropped automatically, but you can manually drop them:
  ```sql
  DROP TABLE #temp_employees;
  ```

---

### **6. Common Use Cases**

1. **Simplifying Complex Queries:**  
   Use a temporary table to store intermediate results for easier manipulation:

   ```sql
   SELECT department, AVG(salary) AS avg_salary
   INTO #temp_avg_salary
   FROM employees
   GROUP BY department;

   SELECT *
   FROM #temp_avg_salary
   WHERE avg_salary > 60000;
   ```

2. **Reducing Query Redundancy:**  
   Avoid repeating the same subquery:

   ```sql
   SELECT emp_id, name, salary
   INTO #temp_high_earners
   FROM employees
   WHERE salary > (SELECT AVG(salary) FROM employees);

   SELECT * FROM #temp_high_earners;
   ```

3. **Handling Large Data Sets:**  
   Temporary tables can be used to break down large data operations into smaller, manageable steps.

---

### **7. Limitations of Temporary Tables**

- Limited to the session or scope in which they are created.
- Not suited for permanent data storage.
- Excessive use can impact `tempdb` performance.

---

### **8. Best Practices**

- Use appropriate data types to reduce storage usage.
- Index temporary tables if necessary for performance optimization.
- Avoid overusing global temporary tables as they can lead to conflicts in multi-user environments.

---

### **9. Exercises**

1. **Basic Temporary Table Creation:**  
   Create a temporary table to store student information and insert sample data into it.

2. **Populating with Query Results:**  
   Create a temporary table containing employees with salaries above $50,000.

3. **Data Analysis:**  
   Use a temporary table to calculate and display department-wise total sales.

4. **Global Temporary Table:**  
   Create a global temporary table shared between multiple sessions.
