# Postgres JOINS (Customer & Orders Example with PK/FK)

## Learning Objectives

Able to...

1. Understand INNER, LEFT, RIGHT, and FULL JOINS in PostgreSQL

---

## Model 1

**Customers**

| customer_id | customer_name |
| ----------- | ------------- |
| c1          | Alice         |
| c2          | Bob           |
| c3          | Carol         |
| c4          | David         |

**Orders**

| order_id | customer_id |
| -------- | ----------- |
| o1       | c1          |
| o2       | c2          |
| o5       | c5          |
| o6       | c6          |

Questions

1. Which customers have matching orders?
   c1 & c2
2. Which customers do not have any orders?
    c3 & c4
3. Which orders do not match any existing customers?
   o5 & o6

---

## Model 2

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
INNER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1	        | Alice	        | o1       |
| c2	        | Bob	          | o2       |

Questions

1. Which customers are not included in the result?
     c3-Carol & c4-David
2. Why do you think they are not in the result?
     because they dont have any orders
3. Which orders are not included in the result?
    o5 & o6
4. Why do you think they are not in the result?
    because they are not existing in the customers table
5. When is a row from Customers or Orders included?
     when the data is existing in both the tables and matched the query of
6. What is the meaning of INNER JOIN?
   It combines rows from two or more tables based on the given query.

---

## Model 3

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
LEFT OUTER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
| c3	        | Carol	        |          |
| c4	        | David	        |          |

Questions

1. Which customers are not included in the result?
   All the customers are included
2. Which orders are not included in the result?
   Orders o5 & o6
3. When is a row included?
   row is included, if a row in the customers table has a matching customer_id in the Orders table
4. What is the meaning of LEFT OUTER JOIN?
   left outer join returns all rows from the left table and matching tables from the right table.

---

## Model 4

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
RIGHT OUTER JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
|   	        |      	        | o5       |
|   	        |     	        | o6       |


Questions

1. Which customers are not included in the result?
   Customers Carol & David
2. Which orders are not included in the result?
   All the orders are included
3. When is a row included?
   A row is included if it comes from Orders table with matching customer data included
4. What is the meaning of RIGHT OUTER JOIN?
   Right Outer Join returns all rows from the right-hand table and any matching rows from the left-hand table

---

## Model 5

Query

```sql
SELECT c.customer_id, c.customer_name, o.order_id
FROM Customers c
FULL JOIN Orders o ON c.customer_id = o.customer_id;
```

Result
| customer_id | customer_name | order_id |
| ----------- | ------------- | -------- |
| c1          | Alice	        | o1       |
| c2	        | Bob	          | o2       |
| c3	        | Carol	        |          |
| c4	        | David	        |          |
|   	        |      	        | o5       |
|   	        |     	        | o6       |

Questions

1. Which customers are not included in the result?
   All the customers are included in the result, Customers with Order_id 5&6 data is not available
2. Which orders are not included in the result?
   All the orders are included
3. When is a row included?
   row is included when it exists in both the tables
4. What is the meaning of FULL JOIN?
   Full Join returns all the rows from both the left table and right table
---

## Model 6

Confirm the above by creating the tables in Postgres and running the queries. Paste the SQL for creating and populating the tables below.

```sql

 #Customers Table
CREATE TABLE Customers (   customer_id VARCHAR(10) PRIMARY KEY,
   customer_name VARCHAR(50)
    );

 #Orders Table
  CREATE TABLE Orders (
   order_id VARCHAR(10) PRIMARY KEY,
   customer_id VARCHAR(10),
  );


 # Inserting Data into Customers table
    INSERT INTO Customers (customer_id,   customer_name) VALUES
     ('c1', 'Alice'),
     ('c2', 'Bob'),
      ('c3', 'Carol'),
      ('c4', 'David');

  # Inserting Data into Orders table
     INSERT INTO Orders (order_id, customer_id) VALUES
      ('o1', 'c1'),
       ('o2', 'c2'),
       ('o5', 'c5'),
      ('o6', 'c6');


 # Inner Join Query
   SELECT c.customer_id, c.customer_name, o.order_id
   FROM Customers c
    INNER JOIN Orders o ON c.customer_id = o.customer_id;

# Left Join query
   SELECT c.customer_id, c.customer_name, o.order_id
    FROM Customers c
    LEFT JOIN Orders o ON c.customer_id = o.customer_id;

# Right Join Query
   SELECT c.customer_id, c.customer_name, o.order_id
   FROM Customers c
    RIGHT JOIN Orders o ON c.customer_id = o.customer_id;

# Full Join
   SELECT c.customer_id, c.customer_name, o.order_id
   FROM Customers c
   FULL JOIN Orders o ON c.customer_id = o.customer_id;


```
