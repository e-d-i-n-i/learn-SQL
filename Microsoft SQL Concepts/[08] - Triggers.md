### **1. Introduction to Triggers**

- **Definition**: A **trigger** is a special type of stored procedure that automatically runs when an event occurs in the database (e.g., `INSERT`, `UPDATE`, or `DELETE`).
- **Types of Triggers in SQL Server**:
  - **DML Triggers**: Triggered by Data Manipulation Language statements like `INSERT`, `UPDATE`, `DELETE`.
  - **DDL Triggers**: Triggered by Data Definition Language statements like `CREATE`, `ALTER`, `DROP`.
  - **LOGON Triggers**: Triggered by a `LOGON` event.

---

### **2. Syntax for Creating Triggers**

```sql
CREATE TRIGGER trigger_name
ON table_name
AFTER | INSTEAD OF [INSERT, UPDATE, DELETE]
AS
BEGIN
    -- Trigger logic
END;
```

**Key Points**:

- `AFTER`: Executes after the triggering event.
- `INSTEAD OF`: Replaces the triggering event.
- Triggers are associated with tables or views.

---

### **3. DML Triggers**

#### **3.1. AFTER Trigger Example**

- **Task**: Log changes made to an `Employees` table.

```sql
CREATE TABLE EmployeeAudit (
    AuditID INT IDENTITY PRIMARY KEY,
    EmployeeID INT,
    Action NVARCHAR(50),
    ActionDate DATETIME DEFAULT GETDATE()
);

CREATE TRIGGER trg_AfterInsert
ON Employees
AFTER INSERT
AS
BEGIN
    INSERT INTO EmployeeAudit (EmployeeID, Action)
    SELECT EmployeeID, 'INSERT'
    FROM inserted;
END;
```

#### **3.2. INSTEAD OF Trigger Example**

- **Task**: Prevent deletion of important employees.

```sql
CREATE TRIGGER trg_InsteadOfDelete
ON Employees
INSTEAD OF DELETE
AS
BEGIN
    PRINT 'Deletion is not allowed on this table!';
END;
```

---

### **4. DDL Triggers**

#### **4.1. Prevent Dropping Tables**

- **Task**: Log or prevent table drops.

```sql
CREATE TRIGGER trg_PreventDrop
ON DATABASE
FOR DROP_TABLE
AS
BEGIN
    PRINT 'Dropping tables is not allowed!';
    ROLLBACK;
END;
```

---

### **5. LOGON Triggers**

#### **5.1. Restrict Certain Logins**

- **Task**: Block a specific user from logging in.

```sql
CREATE TRIGGER trg_BlockLogin
ON ALL SERVER
FOR LOGON
AS
BEGIN
    IF ORIGINAL_LOGIN() = 'BlockedUser'
    BEGIN
        ROLLBACK;
    END;
END;
```

---

### **6. Understanding `inserted` and `deleted` Tables**

- These are **virtual tables** used in triggers:
  - **`inserted`**: Holds the new rows for `INSERT` or `UPDATE` operations.
  - **`deleted`**: Holds the old rows for `DELETE` or `UPDATE` operations.

#### Example:

```sql
CREATE TRIGGER trg_UpdateAudit
ON Employees
AFTER UPDATE
AS
BEGIN
    INSERT INTO EmployeeAudit (EmployeeID, Action)
    SELECT EmployeeID, 'UPDATE'
    FROM inserted;
END;
```

---

### **7. Managing and Debugging Triggers**

- **Disable a Trigger**:
  ```sql
  DISABLE TRIGGER trg_AfterInsert ON Employees;
  ```
- **Enable a Trigger**:
  ```sql
  ENABLE TRIGGER trg_AfterInsert ON Employees;
  ```
- **Drop a Trigger**:
  ```sql
  DROP TRIGGER trg_AfterInsert ON Employees;
  ```

---

### **8. Best Practices for Using Triggers**

1. Keep triggers simple and efficient to avoid performance bottlenecks.
2. Use triggers only when necessary; consider alternatives like constraints or procedures.
3. Avoid cascading triggers to reduce complexity.
4. Document triggers for better maintainability.

---

### **9. Exercises**

1. Create a trigger that logs every deletion from the `Orders` table.
2. Write a trigger to update a total sales column in a `Products` table after an `Orders` table update.
3. Implement a `LOGON` trigger to log all login attempts to a table.

---

### **10. Additional Resources**

- Official Microsoft Documentation: [Triggers in SQL Server](https://learn.microsoft.com/en-us/sql/t-sql/statements/create-trigger-transact-sql)
- Practice Platforms:
  - [SQL Server Management Studio (SSMS)](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms)
  - [Azure Data Studio](https://learn.microsoft.com/en-us/sql/azure-data-studio/what-is)
