# 📊 **SQL Review: Simple SELECT Queries**

Congratulations on making it this far! In this review, you’ll practice writing **SELECT queries** that solve real-world problems using a table of data. This will help you get comfortable with combining different SQL clauses to retrieve specific information.

---

## 🔎 **SELECT Query Syntax**

The general format of a **SELECT** query is:

```sql
SELECT column, another_column, ...
FROM mytable
WHERE condition(s)
ORDER BY column ASC/DESC
LIMIT num_limit OFFSET num_offset;
```

By combining these clauses, you can retrieve, filter, sort, and limit the data that you need.

---

## 🌎 **North American Cities Table**

The table below contains data about some of the most populous cities in North America, including their population and geographical location (latitude and longitude).

| **city**            | **country**   | **population** | **latitude** | **longitude** |
| ------------------- | ------------- | -------------- | ------------ | ------------- |
| Guadalajara         | Mexico        | 1,500,800      | 20.659699    | -103.349609   |
| Toronto             | Canada        | 2,795,060      | 43.653226    | -79.383184    |
| Houston             | United States | 2,195,914      | 29.760427    | -95.369803    |
| New York            | United States | 8,405,837      | 40.712784    | -74.005941    |
| Philadelphia        | United States | 1,553,165      | 39.952584    | -75.165222    |
| Havana              | Cuba          | 2,106,146      | 23.054070    | -82.345189    |
| Mexico City         | Mexico        | 8,555,500      | 19.432608    | -99.133208    |
| Phoenix             | United States | 1,513,367      | 33.448377    | -112.074037   |
| Los Angeles         | United States | 3,884,307      | 34.052234    | -118.243685   |
| Ecatepec de Morelos | Mexico        | 1,742,000      | 19.601841    | -99.050674    |
| Montreal            | Canada        | 1,717,767      | 45.501689    | -73.567256    |
| Chicago             | United States | 2,718,782      | 41.878114    | -87.629798    |

---

## 📝 **Review 1 — Tasks**

Use the **north_american_cities** table to complete the following tasks:

---

### 1️⃣ **List all the Canadian cities and their populations**

To retrieve all Canadian cities and their populations, we can use the following query:

```sql
SELECT city, population
FROM north_american_cities
WHERE country = 'Canada';
```

---

### 2️⃣ **Order all the cities in the United States by their latitude from north to south**

To order cities in the U.S. based on latitude from north to south, use this query:

```sql
SELECT city, latitude
FROM north_american_cities
WHERE country = 'United States'
ORDER BY latitude DESC;
```

---

### 3️⃣ **List all the cities west of Chicago, ordered from west to east**

To find cities west of Chicago (i.e., cities with a longitude less than Chicago's longitude) and order them from west to east:

```sql
SELECT city, longitude
FROM north_american_cities
WHERE longitude < -87.629798
ORDER BY longitude ASC;
```

---

### 4️⃣ **List the two largest cities in Mexico (by population)**

To find the two largest cities in Mexico by population:

```sql
SELECT city, population
FROM north_american_cities
WHERE country = 'Mexico'
ORDER BY population DESC
LIMIT 2;
```

---

### 5️⃣ **List the third and fourth largest cities (by population) in the United States and their population**

To retrieve the third and fourth largest U.S. cities by population:

```sql
SELECT city, population
FROM north_american_cities
WHERE country = 'United States'
ORDER BY population DESC
LIMIT 2 OFFSET 2;
```

---

## 📈 **Next Steps**

Try these exercises to build your confidence in using **SELECT queries** with different clauses. Once you’re comfortable with these, you’ll be ready to explore more advanced SQL techniques involving multiple tables and more complex queries. 🚀

---
