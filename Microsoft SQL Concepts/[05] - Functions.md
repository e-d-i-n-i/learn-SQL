### **Course Material for Functions in Microsoft SQL Server**

---

### **1. Introduction to Functions**

- **Definition**: A function is a reusable SQL code block that performs a specific task and can return a value.
- **Types of Functions in SQL Server**:
  1. **System Functions**: Predefined by SQL Server (e.g., `GETDATE()`, `LEN()`).
  2. **User-Defined Functions (UDFs)**:
     - **Scalar Functions**: Returns a single value.
     - **Table-Valued Functions (TVFs)**:
       - **Inline**: Returns a table with a single `SELECT` statement.
       - **Multistatement**: Returns a table built using multiple statements.

---

### **2. Syntax for Creating Functions**

#### **Scalar Function Syntax**

```sql
CREATE FUNCTION function_name (@parameter_name data_type)
RETURNS return_data_type
AS
BEGIN
    -- Function logic
    RETURN value;
END;
```

#### **Inline Table-Valued Function Syntax**

```sql
CREATE FUNCTION function_name (@parameter_name data_type)
RETURNS TABLE
AS
RETURN
(
    SELECT columns FROM table WHERE conditions
);
```

#### **Multistatement Table-Valued Function Syntax**

```sql
CREATE FUNCTION function_name (@parameter_name data_type)
RETURNS @table_variable TABLE (column_definition)
AS
BEGIN
    -- Insert data into @table_variable
    RETURN;
END;
```

---

### **3. Scalar Function Examples**

#### **3.1. Calculate Age**

```sql
CREATE FUNCTION dbo.CalculateAge (@birthDate DATE)
RETURNS INT
AS
BEGIN
    RETURN DATEDIFF(YEAR, @birthDate, GETDATE());
END;
```

**Usage**:

```sql
SELECT dbo.CalculateAge('1990-01-01') AS Age;
```

#### **3.2. Convert Temperature**

```sql
CREATE FUNCTION dbo.FahrenheitToCelsius (@fahrenheit FLOAT)
RETURNS FLOAT
AS
BEGIN
    RETURN (@fahrenheit - 32) * 5.0 / 9.0;
END;
```

**Usage**:

```sql
SELECT dbo.FahrenheitToCelsius(98.6) AS Celsius;
```

---

### **4. Inline Table-Valued Function Examples**

#### **4.1. Filter Active Employees**

```sql
CREATE FUNCTION dbo.GetActiveEmployees ()
RETURNS TABLE
AS
RETURN
(
    SELECT EmployeeID, Name, Status
    FROM Employees
    WHERE Status = 'Active'
);
```

**Usage**:

```sql
SELECT * FROM dbo.GetActiveEmployees();
```

---

### **5. Multistatement Table-Valued Function Examples**

#### **5.1. Generate Employee Summary**

```sql
CREATE FUNCTION dbo.EmployeeSummary ()
RETURNS @Summary TABLE (EmployeeID INT, TotalSales DECIMAL(10, 2))
AS
BEGIN
    INSERT INTO @Summary
    SELECT EmployeeID, SUM(SalesAmount)
    FROM Sales
    GROUP BY EmployeeID;

    RETURN;
END;
```

**Usage**:

```sql
SELECT * FROM dbo.EmployeeSummary();
```

---

### **6. System Functions**

1. **String Functions**:

   - `LEN()`: Returns the length of a string.
   - `UPPER()`: Converts a string to uppercase.
   - `LOWER()`: Converts a string to lowercase.

2. **Date and Time Functions**:

   - `GETDATE()`: Returns the current date and time.
   - `DATEADD()`: Adds an interval to a date.
   - `DATEDIFF()`: Calculates the difference between two dates.

3. **Aggregate Functions**:
   - `SUM()`: Calculates the total.
   - `AVG()`: Calculates the average.
   - `COUNT()`: Counts rows.

---

### **7. Modifying and Dropping Functions**

- **Modify a Function**:
  ```sql
  ALTER FUNCTION dbo.FunctionName
  AS
  BEGIN
      -- New logic
  END;
  ```
- **Drop a Function**:
  ```sql
  DROP FUNCTION dbo.FunctionName;
  ```

---

### **8. Exercises**

1. Create a **scalar function** to calculate the square of a number.
2. Write an **inline table-valued function** to return all orders above a specific amount.
3. Create a **multistatement table-valued function** that generates a report of total sales by region.

---

### **9. Best Practices for Functions**

1. Keep functions focused on a single task for clarity.
2. Avoid complex logic in scalar functions to reduce performance overhead.
3. Use table-valued functions for reusable query logic instead of duplicating queries.
4. Document function inputs, outputs, and usage.

---
