# **What Are Objects in SQL?**

## **Definition**

In SQL, **objects** refer to entities or structures within a database that store, manipulate, and interact with data. These objects are the building blocks of a database, and they include tables, views, indexes, triggers, stored procedures, schemas, and more.

---

## **Types of Database Objects**

### **1. Tables**

- **Definition**: A table is the most fundamental object in a database that stores data in rows and columns.
- **Example**:
  ```sql
  CREATE TABLE Employees (
      EmployeeID INT PRIMARY KEY,
      FirstName NVARCHAR(50),
      LastName NVARCHAR(50),
      Department NVARCHAR(50)
  );
  ```

---

### **2. Views**

- **Definition**: A view is a virtual table based on the result of a SQL query. It does not store data but retrieves data from one or more tables.
- **Example**:
  ```sql
  CREATE VIEW vw_EmployeeDetails AS
  SELECT EmployeeID, FirstName, LastName
  FROM Employees;
  ```

---

### **3. Indexes**

- **Definition**: Indexes improve the speed of data retrieval in a table.
- **Example**:
  ```sql
  CREATE NONCLUSTERED INDEX idx_LastName ON Employees (LastName);
  ```

---

### **4. Triggers**

- **Definition**: A trigger is a special type of stored procedure that automatically executes when certain events (INSERT, UPDATE, DELETE) occur on a table.
- **Example**:
  ```sql
  CREATE TRIGGER trg_AuditLog
  ON Employees
  AFTER INSERT
  AS
  BEGIN
      INSERT INTO AuditLog (Action, EmployeeID, Timestamp)
      SELECT 'Insert', EmployeeID, GETDATE()
      FROM inserted;
  END;
  ```

---

### **5. Stored Procedures**

- **Definition**: A stored procedure is a reusable SQL code block that performs specific tasks, such as retrieving or updating data.
- **Example**:
  ```sql
  CREATE PROCEDURE usp_GetEmployeeByID
      @EmployeeID INT
  AS
  BEGIN
      SELECT * FROM Employees WHERE EmployeeID = @EmployeeID;
  END;
  ```

---

### **6. Functions**

- **Definition**: Functions are objects that perform calculations or return a value. They can be user-defined or built-in.
- **Example**:
  ```sql
  CREATE FUNCTION fn_GetFullName(@FirstName NVARCHAR(50), @LastName NVARCHAR(50))
  RETURNS NVARCHAR(100)
  AS
  BEGIN
      RETURN @FirstName + ' ' + @LastName;
  END;
  ```

---

### **7. Schemas**

- **Definition**: A schema is a logical container that groups database objects. It helps organize and manage database objects within the same namespace.
- **Example**:
  ```sql
  CREATE SCHEMA Sales AUTHORIZATION dbo;
  CREATE TABLE Sales.Orders (
      OrderID INT PRIMARY KEY,
      OrderDate DATE
  );
  ```

---

### **8. Constraints**

- **Definition**: Constraints enforce rules on data in a table to ensure accuracy and reliability.
- **Types of Constraints**:
  - **Primary Key**
  - **Foreign Key**
  - **Unique**
  - **Check**
  - **Default**
- **Example**:
  ```sql
  CREATE TABLE Products (
      ProductID INT PRIMARY KEY,
      ProductName NVARCHAR(100) NOT NULL,
      Price DECIMAL(10, 2) CHECK (Price > 0)
  );
  ```

---

### **9. Sequences**

- **Definition**: A sequence generates unique numeric values, often used for primary key auto-incrementing.
- **Example**:
  ```sql
  CREATE SEQUENCE seq_OrderID
  START WITH 1
  INCREMENT BY 1;
  ```

---

## **Why Are Objects Important?**

1. **Data Storage and Organization**: Objects like tables and schemas structure data efficiently.
2. **Data Access and Manipulation**: Objects like views, procedures, and functions simplify data retrieval and updates.
3. **Performance Optimization**: Indexes improve query performance.
4. **Data Integrity**: Constraints and triggers ensure data accuracy and consistency.

---

## **Example: Using Multiple Objects Together**

### Scenario:

You manage a database for a company, and you need to:

1. Store employee data.
2. Automatically log updates to employee records.
3. Retrieve full employee names.

### Implementation:

1. **Create a Table**:

   ```sql
   CREATE TABLE Employees (
       EmployeeID INT PRIMARY KEY,
       FirstName NVARCHAR(50),
       LastName NVARCHAR(50),
       Department NVARCHAR(50)
   );
   ```

2. **Create a Trigger**:

   ```sql
   CREATE TRIGGER trg_LogUpdates
   ON Employees
   AFTER UPDATE
   AS
   BEGIN
       INSERT INTO AuditLog (Action, EmployeeID, Timestamp)
       SELECT 'Update', EmployeeID, GETDATE()
       FROM inserted;
   END;
   ```

3. **Create a Function**:

   ```sql
   CREATE FUNCTION fn_GetFullName(@FirstName NVARCHAR(50), @LastName NVARCHAR(50))
   RETURNS NVARCHAR(100)
   AS
   BEGIN
       RETURN @FirstName + ' ' + @LastName;
   END;
   ```

4. **Retrieve Full Names**:
   ```sql
   SELECT EmployeeID, dbo.fn_GetFullName(FirstName, LastName) AS FullName
   FROM Employees;
   ```

---
