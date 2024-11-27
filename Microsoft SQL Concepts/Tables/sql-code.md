Here’s the **Microsoft SQL Server code** to insert sample data into tables for the examples provided. The data covers employees, departments, and an audit log for tracking updates.

---

### **Create the Tables**

```sql
-- Create the Employees Table
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName NVARCHAR(50),
    LastName NVARCHAR(50),
    Department NVARCHAR(50)
);

-- Create the AuditLog Table
CREATE TABLE AuditLog (
    LogID INT IDENTITY(1,1) PRIMARY KEY,
    Action NVARCHAR(50),
    EmployeeID INT,
    Timestamp DATETIME
);

-- Create the Departments Table
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName NVARCHAR(50),
    DepartmentHead NVARCHAR(50)
);
```

---

### **Insert Sample Data**

```sql
-- Insert Data into Employees Table
INSERT INTO Employees (EmployeeID, FirstName, LastName, Department)
VALUES
(1, 'Alice', 'Johnson', 'IT'),
(2, 'Bob', 'Smith', 'HR'),
(3, 'Carol', 'Davis', 'Finance');

-- Insert Data into AuditLog Table
-- Example: Manual Insert (triggers can populate this automatically)
INSERT INTO AuditLog (Action, EmployeeID, Timestamp)
VALUES
('Insert', 1, GETDATE()),
('Insert', 2, GETDATE()),
('Insert', 3, GETDATE());

-- Insert Data into Departments Table
INSERT INTO Departments (DepartmentID, DepartmentName, DepartmentHead)
VALUES
(1, 'IT', 'John Doe'),
(2, 'HR', 'Jane Smith'),
(3, 'Finance', 'Emily Taylor');
```

---

### **Trigger for Automatic Logging**

You can add a trigger to automatically log changes in the `Employees` table into the `AuditLog` table.

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

---

### **Test the Data and Trigger**

#### Update the `Employees` Table:

```sql
UPDATE Employees
SET Department = 'Marketing'
WHERE EmployeeID = 2;
```

#### Verify the `AuditLog` Table:

```sql
SELECT * FROM AuditLog;
```

---

This script will set up your tables and populate them with data. You can now run queries, use triggers, and test relationships in your database.
