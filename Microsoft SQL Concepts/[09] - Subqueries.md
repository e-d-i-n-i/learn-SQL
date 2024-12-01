## **Course Title:** Understanding Subqueries in SQL

### **Objective:**

- To understand what subqueries are and how to use them in SQL.
- To explore different types of subqueries and their applications in solving real-world database queries.

---

### **1. Introduction to Subqueries**

- **Definition:**  
  A subquery is a query nested within another SQL query. It can be used in SELECT, INSERT, UPDATE, DELETE statements or inside WHERE, HAVING, and FROM clauses.

- **Types of Subqueries:**

  - Single-row subqueries
  - Multiple-row subqueries
  - Correlated subqueries
  - Scalar subqueries

- **When to Use Subqueries:**
  - Filtering data
  - Computing intermediate results
  - Checking existence or membership of rows

---

### **2. Single-Row Subqueries**

- **Syntax:**

  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name = (SELECT column_name FROM another_table WHERE condition);
  ```

- **Examples:**
  - Find employees earning more than the average salary:
    ```sql
    SELECT name
    FROM employees
    WHERE salary > (SELECT AVG(salary) FROM employees);
    ```

---

### **3. Multiple-Row Subqueries**

- **Operators Used:** `IN`, `ANY`, `ALL`
- **Syntax:**

  ```sql
  SELECT column_name
  FROM table_name
  WHERE column_name IN (SELECT column_name FROM another_table WHERE condition);
  ```

- **Examples:**
  - Find customers from cities where sales exceed $10,000:
    ```sql
    SELECT customer_name
    FROM customers
    WHERE city IN (SELECT city FROM sales WHERE total_sales > 10000);
    ```

---

### **4. Correlated Subqueries**

- **Definition:**  
  A subquery that uses values from the outer query.

- **Syntax:**

  ```sql
  SELECT column_name
  FROM table_name AS outer_table
  WHERE condition (SELECT column_name FROM another_table AS inner_table WHERE outer_table.column_name = inner_table.column_name);
  ```

- **Examples:**
  - Find employees earning more than the average salary in their department:
    ```sql
    SELECT name
    FROM employees e1
    WHERE salary > (SELECT AVG(salary) FROM employees e2 WHERE e1.department_id = e2.department_id);
    ```

---

### **5. Scalar Subqueries**

- **Definition:**  
  A subquery that returns exactly one value (a single row and column).

- **Examples:**
  - Fetch the name of the highest-paid employee:
    ```sql
    SELECT name
    FROM employees
    WHERE salary = (SELECT MAX(salary) FROM employees);
    ```

---

### **6. Using Subqueries in Different Clauses**

- **In the `SELECT` Clause:**

  - Add a computed column:
    ```sql
    SELECT name, (SELECT AVG(salary) FROM employees) AS avg_salary
    FROM employees;
    ```

- **In the `FROM` Clause:**

  - Using subqueries as derived tables:
    ```sql
    SELECT dept_name, avg_salary
    FROM (SELECT department_id, AVG(salary) AS avg_salary FROM employees GROUP BY department_id) AS dept_stats;
    ```

- **In the `HAVING` Clause:**
  - Filter aggregated results:
    ```sql
    SELECT department_id, COUNT(*)
    FROM employees
    GROUP BY department_id
    HAVING COUNT(*) > (SELECT AVG(employee_count) FROM (SELECT department_id, COUNT(*) AS employee_count FROM employees GROUP BY department_id) AS sub);
    ```

---

### **7. Best Practices for Writing Subqueries**

- Keep subqueries simple and focused.
- Avoid using subqueries if joins can perform better.
- Use indexed columns for faster subquery execution.
- Prefer using correlated subqueries only when necessary, as they can be slower.

---

### **8. Exercises**

1. **Basic Subquery:**  
   Write a query to find the second-highest salary from an `employees` table.

2. **Correlated Subquery:**  
   Find all students with grades above the average in their class.

3. **Subqueries with Aggregates:**  
   Identify the departments where total salaries exceed the company’s average salary.

4. **Using `IN` and `NOT IN`:**  
   Retrieve product names not sold in the last 30 days.

---
