### **Course Material for Schemas in Microsoft SQL Server**

---

### **1. Introduction to Schemas**

- **Definition**: A schema in SQL Server is a logical container or namespace that holds database objects like tables, views, stored procedures, and functions.
- **Purpose**:
  1. **Organize database objects**.
  2. **Manage permissions**.
  3. **Improve security and development collaboration**.

---

### **2. Default Schema in SQL Server**

- The default schema for a user is usually **`dbo`** (Database Owner).
- A user can have a custom schema to avoid conflicts.

---

### **3. Creating and Managing Schemas**

#### **3.1. Create a Schema**

```sql
CREATE SCHEMA schema_name AUTHORIZATION user_name;
```

**Example**:

```sql
CREATE SCHEMA Sales AUTHORIZATION dbo;
```

#### **3.2. Assign a Schema to an Object**

- Specify the schema when creating objects:

```sql
CREATE TABLE Sales.Orders (
    OrderID INT PRIMARY KEY,
    OrderDate DATE,
    TotalAmount DECIMAL(10, 2)
);
```

---

### **4. Modifying Schemas**

#### **4.1. Transfer an Object to Another Schema**

```sql
ALTER SCHEMA target_schema TRANSFER source_schema.object_name;
```

**Example**:

```sql
ALTER SCHEMA Finance TRANSFER Sales.Orders;
```

#### **4.2. Change Default Schema for a User**

```sql
ALTER USER user_name WITH DEFAULT_SCHEMA = schema_name;
```

**Example**:

```sql
ALTER USER JohnDoe WITH DEFAULT_SCHEMA = Sales;
```

---

### **5. Dropping a Schema**

- A schema must be empty before it can be dropped.

```sql
DROP SCHEMA schema_name;
```

**Example**:

```sql
DROP SCHEMA Sales;
```

---

### **6. Using Schemas for Organization**

- **Scenario**: Separate objects based on functionality or department.
  - **HR Schema**: Contains tables like `Employees`, `Departments`.
  - **Sales Schema**: Contains tables like `Orders`, `Customers`.

---

### **7. Schema Security and Permissions**

- **Grant Schema Permissions**:

```sql
GRANT SELECT ON SCHEMA::schema_name TO user_name;
```

**Example**:

```sql
GRANT SELECT ON SCHEMA::Sales TO Analyst;
```

- **Revoke Schema Permissions**:

```sql
REVOKE SELECT ON SCHEMA::schema_name FROM user_name;
```

- **Deny Schema Permissions**:

```sql
DENY SELECT ON SCHEMA::schema_name TO user_name;
```

---

### **8. Schema Best Practices**

1. **Use schemas for grouping**: Group related objects to improve database organization.
2. **Assign schemas per team**: Delegate responsibility to different development teams or departments.
3. **Use schemas for security**: Limit access to sensitive objects using schemas.
4. **Avoid over-segmenting**: Keep the schema structure simple and logical.

---

### **9. Exercises**

1. Create a schema called `Finance` and add a table `Budget` to it.
2. Move an existing table from the `dbo` schema to the `HR` schema.
3. Grant `SELECT` and `INSERT` permissions on the `Sales` schema to a user `JohnDoe`.

---
