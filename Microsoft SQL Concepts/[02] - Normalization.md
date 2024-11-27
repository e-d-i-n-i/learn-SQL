# **What is Normalization?**

## **Definition**

**Normalization** is the process of organizing data in a database to minimize redundancy (duplicate data) and ensure data integrity. It involves dividing a database into smaller, related tables and defining relationships between them.

The goal of normalization is to:

- Reduce redundancy.
- Improve data consistency.
- Optimize database performance.

---

## **The Normal Forms (NF)**

### **1. First Normal Form (1NF)**

A table is in 1NF if:

1. Each cell contains a single value (no repeating groups or arrays).
2. Each row is unique, typically ensured by a primary key.

#### **Example:**

Unnormalized Table:
| StudentID | Name | Subjects |
|-----------|------------|-------------------|
| 1 | Alice | Math, Science |
| 2 | Bob | History, Geography|

Normalized (1NF) Table:
| StudentID | Name | Subject |
|-----------|------------|-------------|
| 1 | Alice | Math |
| 1 | Alice | Science |
| 2 | Bob | History |
| 2 | Bob | Geography |

---

### **2. Second Normal Form (2NF)**

A table is in 2NF if:

1. It is in 1NF.
2. All non-key columns depend on the entire primary key (no partial dependency).

#### **Example:**

1NF Table:
| StudentID | Subject | Teacher | Department |
|-----------|-------------|--------------|-------------|
| 1 | Math | Mr. Smith | Science |
| 1 | Science | Dr. Taylor | Science |
| 2 | History | Ms. Brown | Arts |

Issues:

- `Department` depends on `Subject`, not the full `StudentID + Subject` key.

2NF Table (Separate Subjects Table):
| Subject | Teacher | Department |
|-------------|--------------|-------------|
| Math | Mr. Smith | Science |
| Science | Dr. Taylor | Science |
| History | Ms. Brown | Arts |

| StudentID | Subject |
| --------- | ------- |
| 1         | Math    |
| 1         | Science |
| 2         | History |

---

### **3. Third Normal Form (3NF)**

A table is in 3NF if:

1. It is in 2NF.
2. There are no transitive dependencies (non-key columns depend only on the primary key).

#### **Example:**

2NF Table:
| SubjectID | Subject | Department | DepartmentHead |
|-----------|-------------|------------|----------------|
| 1 | Math | Science | Dr. Green |
| 2 | History | Arts | Dr. White |

Issues:

- `DepartmentHead` depends on `Department`, not on `SubjectID`.

3NF Table (Separate Department Table):
| Department | DepartmentHead |
|------------|----------------|
| Science | Dr. Green |
| Arts | Dr. White |

| SubjectID | Subject | Department |
| --------- | ------- | ---------- |
| 1         | Math    | Science    |
| 2         | History | Arts       |

---

## **Benefits of Normalization**

1. **Reduces Data Redundancy:** Prevents duplicate data in multiple places.
2. **Improves Data Integrity:** Ensures data consistency across related tables.
3. **Easier Maintenance:** Simplifies updates and reduces errors.
4. **Optimizes Storage:** Saves disk space by removing redundant data.

---

## **When to Denormalize?**

While normalization is beneficial, there are cases where **denormalization** (combining tables for performance) is used to:

- Speed up read-heavy operations.
- Reduce the need for complex joins.

---

## **Practice Example**

### Scenario:

You manage a **School** database with the following data:

| StudentID | Name  | Course1 | Course2   | Teacher   |
| --------- | ----- | ------- | --------- | --------- |
| 1         | Alice | Math    | Science   | Mr. Smith |
| 2         | Bob   | History | Geography | Ms. Brown |

**Task:**
Normalize this table into 3NF.

**Solution:**

1. **1NF:** Break repeating columns into rows.
2. **2NF:** Separate data into `Students` and `Courses` tables.
3. **3NF:** Create a `Teachers` table for teacher-related data.

---
