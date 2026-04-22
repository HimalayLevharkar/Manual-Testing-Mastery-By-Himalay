# 21_SQL_For_Testers

## SQL for Software Testers
### Complete Guide to SQL for Testing with Real-World Examples

---

## 📋 Table of Contents

1. [Why SQL Matters for Testers](#why)
2. [SQL Basics](#basics)
3. [SELECT Statement Deep Dive](#select)
4. [WHERE Clause & Filtering](#where)
5. [JOINs for Testers](#joins)
6. [Aggregate Functions](#aggregate)
7. [GROUP BY & HAVING](#groupby)
8. [Subqueries](#subqueries)
9. [Data Validation Testing](#validation)
10. [Database Testing Scenarios](#scenarios)
11. [SQL for Test Data Management](#testdata)
12. [Real Testing Scenarios](#real)
13. [SQL Test Cases](#test-cases)
14. [Interview Questions](#interview)

---

## 💡 Why SQL Matters for Testers {#why}

### Why Testers Need SQL?

```
Real-World Testing Scenarios Where SQL is Essential:

📊 Data Validation
   - Verify data saved correctly in database
   - Check data integrity after operations
   - Validate calculations and aggregations

🔍 Defect Investigation
   - Find root cause of issues
   - Check data corruption
   - Analyze production issues

✅ Test Data Setup
   - Create test data directly in database
   - Reset test environment
   - Generate specific test scenarios

📈 Reporting & Analysis
   - Extract test execution data
   - Analyze defect patterns
   - Create metrics dashboards

🔐 Security Testing
   - SQL injection testing
   - Access control verification
   - Data encryption verification
```

### Where Testers Use SQL

```
Daily Testing Activities:

┌─────────────────────────────────────────────────┐
│ 1. Verifying UI Data with Database             │
│    - User creates record in UI                 │
│    - Tester verifies in database               │
│    - Ensures data integrity                    │
├─────────────────────────────────────────────────┤
│ 2. Backend Data Validation                     │
│    - API returns data                          │
│    - Verify against database                   │
│    - Ensure API accuracy                       │
├─────────────────────────────────────────────────┤
│ 3. Test Data Preparation                       │
│    - Need specific data for testing            │
│    - Insert directly via SQL                   │
│    - Faster than UI creation                   │
├─────────────────────────────────────────────────┤
│ 4. Data Migration Testing                      │
│    - Compare old vs new database               │
│    - Verify data transferred correctly         │
│    - Check data transformations                │
├─────────────────────────────────────────────────┤
│ 5. ETL Testing                                 │
│    - Source to target validation               │
│    - Transformation verification               │
│    - Data quality checks                       │
├─────────────────────────────────────────────────┤
│ 6. Defect Investigation                        │
│    - User reports issue                        │
│    - Query database to find root cause         │
│    - Reproduce and fix                         │
└─────────────────────────────────────────────────┘
```

### SQL in Different Testing Types

```
┌──────────────────────┬─────────────────────────────────────┐
│ Testing Type         │ SQL Usage                           │
├──────────────────────┼─────────────────────────────────────┤
│ Functional Testing   │ Verify data saved correctly         │
│ Database Testing     │ Direct database validation          │
│ ETL Testing          │ Source-target comparison            │
│ Data Migration       │ Before/after data comparison        │
│ Security Testing     │ SQL injection, access control       │
│ Performance Testing  │ Query performance analysis          │
│ Integration Testing  │ Cross-system data validation        │
│ Regression Testing   │ Data integrity verification         │
└──────────────────────┴─────────────────────────────────────┘
```

---

## 📚 SQL Basics {#basics}

### What is SQL?

**SQL (Structured Query Language)** - Database se communicate karne ke liye standard language.

### SQL Command Categories

```
                    SQL COMMANDS
                        │
        ┌───────────────┼───────────────┐
        │               │               │
        DDL             DML             DCL
        │               │               │
        │               │               │
    Structure       Data          Access
    Definition      Manipulation    Control
    
    CREATE          SELECT          GRANT
    ALTER           INSERT          REVOKE
    DROP            UPDATE
    TRUNCATE        DELETE
```

### DDL (Data Definition Language)

```
Purpose: Database structure define/change karna

Commands:

1. CREATE - New table/database banana
   CREATE TABLE users (
       id INT PRIMARY KEY,
       name VARCHAR(100),
       email VARCHAR(100)
   );

2. ALTER - Existing table modify karna
   ALTER TABLE users ADD phone VARCHAR(20);

3. DROP - Table delete karna (structure + data)
   DROP TABLE users;

4. TRUNCATE - Table data delete karna (structure remains)
   TRUNCATE TABLE users;
```

### DML (Data Manipulation Language)

```
Purpose: Database mein data manipulate karna

Commands:

1. SELECT - Data retrieve karna
   SELECT * FROM users;

2. INSERT - New data add karna
   INSERT INTO users (id, name, email) 
   VALUES (1, 'John', 'john@example.com');

3. UPDATE - Existing data modify karna
   UPDATE users SET email = 'new@example.com' 
   WHERE id = 1;

4. DELETE - Data delete karna
   DELETE FROM users WHERE id = 1;
```

### DCL (Data Control Language)

```
Purpose: Database access control karna

Commands:

1. GRANT - Permissions dena
   GRANT SELECT ON users TO tester;

2. REVOKE - Permissions wapas lena
   REVOKE SELECT ON users FROM tester;
```

### Database Tables - Basic Structure

```
Example: users table

┌────┬──────────┬───────────────────┬─────────────┬
│ id │ name     │ email             │ created_at  │
├────┼──────────┼───────────────────┼─────────────┤
│ 1  │ John     │ john@test.com     │ 2026-01-01  │
│ 2  │ Jane     │ jane@test.com     │ 2026-01-02  │
│ 3  │ Bob      │ bob@test.com      │ 2026-01-03  │
└────┴──────────┴───────────────────┴─────────────┘

Terminology:
- Table/Relation: users
- Row/Record: Single entry (e.g., John's data)
- Column/Field: Attribute (e.g., name, email)
- Primary Key: Unique identifier (id)
```

---

## 🔍 SELECT Statement Deep Dive {#select}

### Basic SELECT Syntax

```
Syntax:
SELECT column1, column2, ...
FROM table_name;

Examples:

-- Select specific columns
SELECT name, email FROM users;

-- Select all columns
SELECT * FROM users;

-- Select with alias
SELECT name AS user_name, email AS user_email 
FROM users;
```

### SELECT DISTINCT

```
Purpose: Duplicate values remove karna

Syntax:
SELECT DISTINCT column_name FROM table_name;

Example:
-- Get all unique cities from customers
SELECT DISTINCT city FROM customers;

-- Get unique status from orders
SELECT DISTINCT status FROM orders;

Real Testing Scenario:
Q: Check if any duplicate emails exist in users table
A: 
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### SELECT with LIMIT/TOP

```
Purpose: Limited rows return karna

Syntax (varies by database):

-- MySQL, PostgreSQL
SELECT * FROM users LIMIT 5;

-- SQL Server
SELECT TOP 5 * FROM users;

-- Oracle
SELECT * FROM users WHERE ROWNUM <= 5;

Real Testing Scenario:
Q: Check first 10 records for data quality
A: SELECT * FROM users LIMIT 10;
```

### SELECT with ORDER BY

```
Purpose: Results sort karna

Syntax:
SELECT column1, column2
FROM table_name
ORDER BY column1 [ASC|DESC];

Examples:
-- Sort by name (ascending)
SELECT * FROM users ORDER BY name ASC;

-- Sort by created date (newest first)
SELECT * FROM orders ORDER BY created_at DESC;

-- Multiple column sorting
SELECT * FROM orders 
ORDER BY status ASC, created_at DESC;

Real Testing Scenario:
Q: Find most recent orders
A: 
SELECT * FROM orders 
ORDER BY created_at DESC 
LIMIT 20;
```

---

## 🎯 WHERE Clause & Filtering {#where}

### WHERE Clause Basics

```
Purpose: Specific conditions ke basis par rows filter karna

Syntax:
SELECT column1, column2
FROM table_name
WHERE condition;

Examples:
-- Get user by ID
SELECT * FROM users WHERE id = 1;

-- Get users by name
SELECT * FROM users WHERE name = 'John';

-- Get active users
SELECT * FROM users WHERE status = 'active';
```

### Comparison Operators

```
Operator    Meaning         Example
─────────────────────────────────────────
=           Equal           WHERE age = 25
<> or !=    Not Equal       WHERE status != 'inactive'
>           Greater than    WHERE salary > 50000
<           Less than       WHERE age < 18
>=          Greater/equal   WHERE created_at >= '2026-01-01'
<=          Less/equal      WHERE price <= 100
```

### Logical Operators

```
1. AND - Both conditions true honi chahiye

SELECT * FROM users 
WHERE age > 18 AND status = 'active';

2. OR - Either condition true ho sakti hai

SELECT * FROM users 
WHERE status = 'active' OR status = 'pending';

3. NOT - Condition false honi chahiye

SELECT * FROM users 
WHERE NOT status = 'deleted';

Real Testing Scenario:
Q: Find active users above 18 years
A: 
SELECT * FROM users 
WHERE age > 18 AND status = 'active';
```

### IN Operator

```
Purpose: Multiple values check karna

Syntax:
SELECT * FROM table WHERE column IN (value1, value2, ...);

Examples:
-- Get users from specific cities
SELECT * FROM users 
WHERE city IN ('Delhi', 'Mumbai', 'Bangalore');

-- Get orders with specific statuses
SELECT * FROM orders 
WHERE status IN ('pending', 'processing', 'shipped');

Equivalent to:
WHERE city = 'Delhi' OR city = 'Mumbai' OR city = 'Bangalore'
```

### BETWEEN Operator

```
Purpose: Range check karna

Syntax:
SELECT * FROM table WHERE column BETWEEN value1 AND value2;

Examples:
-- Get orders in date range
SELECT * FROM orders 
WHERE order_date BETWEEN '2026-01-01' AND '2026-01-31';

-- Get products in price range
SELECT * FROM products 
WHERE price BETWEEN 100 AND 500;

-- Get employees in salary range
SELECT * FROM employees 
WHERE salary BETWEEN 30000 AND 80000;

Real Testing Scenario:
Q: Find all transactions in last month
A: 
SELECT * FROM transactions 
WHERE transaction_date BETWEEN '2025-12-01' AND '2025-12-31';
```

### LIKE Operator (Pattern Matching)

```
Purpose: Pattern-based search karna

Wildcards:
% - Zero or more characters
_ - Single character

Examples:
-- Names starting with 'J'
SELECT * FROM users WHERE name LIKE 'J%';

-- Names ending with 'h'
SELECT * FROM users WHERE name LIKE '%h';

-- Names containing 'oh'
SELECT * FROM users WHERE name LIKE '%oh%';

-- Names with exactly 4 characters
SELECT * FROM users WHERE name LIKE '____';

-- Email validation check
SELECT * FROM users WHERE email LIKE '%@%.%';

Real Testing Scenario:
Q: Find all users with Gmail emails
A: 
SELECT * FROM users 
WHERE email LIKE '%@gmail.com';
```

### IS NULL Operator

```
Purpose: NULL values check karna

Examples:
-- Find records with NULL values
SELECT * FROM users WHERE phone IS NULL;

-- Find records with NOT NULL values
SELECT * FROM users WHERE phone IS NOT NULL;

-- Find incomplete records
SELECT * FROM users 
WHERE email IS NULL OR phone IS NULL;

Important:
⚠ NULL = NULL doesn't work!
⚠ Always use IS NULL or IS NOT NULL
```

### Complex WHERE Conditions

```
Real Testing Scenarios:

Scenario 1: Find inactive users with pending orders
SELECT * FROM users u
JOIN orders o ON u.id = o.user_id
WHERE u.status = 'inactive' 
  AND o.status = 'pending';

Scenario 2: Find high-value customers
SELECT * FROM customers 
WHERE total_orders > 10 
  AND total_spent > 50000
  AND status = 'active';

Scenario 3: Find suspicious transactions
SELECT * FROM transactions 
WHERE amount > 100000
  AND status = 'completed'
  AND created_at BETWEEN '2026-01-01 00:00:00' 
                     AND '2026-01-01 23:59:59';
```

---

## 🔗 JOINs for Testers {#joins}

### Why JOINs are Important for Testers?

```
Real Testing Scenarios:

✓ Data across multiple tables verify karna
✓ Referential integrity check karna
✓ Complex queries for defect investigation
✓ ETL testing - source to target mapping
✓ API response validation with database
```

### Types of JOINs

```
                    JOIN TYPES
                        │
        ┌───────────────┼───────────────┐
        │               │               │
     INNER           LEFT            RIGHT
     JOIN            JOIN            JOIN
        │               │               │
        │               │               │
    Matching        All left +      All right +
    rows only       matching        matching
```

### INNER JOIN

```
Purpose: Sirf matching rows return karna

Syntax:
SELECT columns
FROM table1
INNER JOIN table2 ON table1.column = table2.column;

Example:
-- Get users with their orders
SELECT u.name, u.email, o.order_id, o.amount
FROM users u
INNER JOIN orders o ON u.id = o.user_id;

Visual:
Users:          Orders:
1 John      ──→  101 (user_id=1)
2 Jane      ──→  102 (user_id=1)
3 Bob            103 (user_id=2)
                 104 (user_id=5) ← No match

Result: Only John and Jane's orders (matching records)
```

### LEFT JOIN (LEFT OUTER JOIN)

```
Purpose: All left table rows + matching right table rows

Syntax:
SELECT columns
FROM table1
LEFT JOIN table2 ON table1.column = table2.column;

Example:
-- Get all users and their orders (including users without orders)
SELECT u.name, u.email, o.order_id, o.amount
FROM users u
LEFT JOIN orders o ON u.id = o.user_id;

Visual:
Users:          Orders:
1 John      ──→  101 (user_id=1)
2 Jane      ──→  102 (user_id=1)
3 Bob            103 (user_id=2)
                 104 (user_id=5)

Result: All users + their orders (Bob shows with NULL order)

Real Testing Scenario:
Q: Find users who have NOT placed any orders
A: 
SELECT u.name, u.email
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE o.order_id IS NULL;
```

### RIGHT JOIN (RIGHT OUTER JOIN)

```
Purpose: All right table rows + matching left table rows

Syntax:
SELECT columns
FROM table1
RIGHT JOIN table2 ON table1.column = table2.column;

Example:
-- Get all orders and user details (including orphaned orders)
SELECT u.name, u.email, o.order_id, o.amount
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id;

Visual:
Users:          Orders:
1 John      ──→  101 (user_id=1)
2 Jane      ──→  102 (user_id=1)
                 103 (user_id=2)
                 104 (user_id=5) ← No user match

Result: All orders + user details (order 104 shows with NULL user)

Real Testing Scenario:
Q: Find orphaned orders (orders without valid user)
A: 
SELECT o.order_id, o.user_id, o.amount
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id
WHERE u.id IS NULL;
```

### FULL OUTER JOIN

```
Purpose: All rows from both tables

Syntax:
SELECT columns
FROM table1
FULL OUTER JOIN table2 ON table1.column = table2.column;

Note: MySQL mein FULL OUTER JOIN directly support nahi hai.
UNION use karna padta hai.

Example:
-- Get all users and all orders (complete data)
SELECT u.name, o.order_id
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
UNION ALL
SELECT u.name, o.order_id
FROM users u
RIGHT JOIN orders o ON u.id = o.user_id;

Result: 
- Users with orders
- Users without orders
- Orders without users
```

### SELF JOIN

```
Purpose: Table ko khud se join karna

Example:
-- Find employees and their managers
SELECT e.name AS employee, m.name AS manager
FROM employees e
LEFT JOIN employees m ON e.manager_id = m.id;

Visual:
Employees:
1 John (manager_id=NULL)
2 Jane (manager_id=1)
3 Bob (manager_id=1)
4 Alice (manager_id=2)

Result:
Employee │ Manager
─────────┼────────
Jane     │ John
Bob      │ John
Alice    │ Jane
```

### Multiple JOINs

```
Purpose: Multiple tables se data lana

Example:
-- Get user, order, and product details
SELECT u.name, o.order_id, p.product_name, oi.quantity
FROM users u
INNER JOIN orders o ON u.id = o.user_id
INNER JOIN order_items oi ON o.id = oi.order_id
INNER JOIN products p ON oi.product_id = p.id;

Real Testing Scenario:
Q: Complete order details for report
A: 
SELECT 
    u.name AS customer_name,
    u.email,
    o.order_id,
    o.order_date,
    p.product_name,
    oi.quantity,
    oi.price,
    (oi.quantity * oi.price) AS line_total
FROM users u
INNER JOIN orders o ON u.id = o.user_id
INNER JOIN order_items oi ON o.id = oi.order_id
INNER JOIN products p ON oi.product_id = p.id
WHERE o.order_id = 12345;
```

---

## 📊 Aggregate Functions {#aggregate}

### What are Aggregate Functions?

Multiple rows par calculation karke single value return karna.

### COUNT Function

```
Purpose: Row count karna

Examples:
-- Total users count
SELECT COUNT(*) FROM users;

-- Count users with email
SELECT COUNT(email) FROM users;

-- Count unique cities
SELECT COUNT(DISTINCT city) FROM users;

Real Testing Scenario:
Q: Verify total records after data migration
A: SELECT COUNT(*) FROM users;
```

### SUM Function

```
Purpose: Values ka total calculate karna

Examples:
-- Total sales
SELECT SUM(amount) FROM orders;

-- Total quantity sold
SELECT SUM(quantity) FROM order_items;

-- Total salary paid
SELECT SUM(salary) FROM employees;

Real Testing Scenario:
Q: Verify daily sales total
A: 
SELECT SUM(amount) AS total_sales 
FROM orders 
WHERE order_date = '2026-01-15';
```

### AVG Function

```
Purpose: Average calculate karna

Examples:
-- Average order value
SELECT AVG(amount) FROM orders;

-- Average salary
SELECT AVG(salary) FROM employees;

-- Average product rating
SELECT AVG(rating) FROM product_reviews;

Real Testing Scenario:
Q: Check if average order value increased
A: 
SELECT AVG(amount) AS avg_order_value 
FROM orders 
WHERE order_date >= '2026-01-01';
```

### MIN/MAX Functions

```
Purpose: Minimum/Maximum value dhundhna

Examples:
-- Highest salary
SELECT MAX(salary) FROM employees;

-- Lowest order amount
SELECT MIN(amount) FROM orders;

-- Most recent order
SELECT MAX(order_date) FROM orders;

-- Oldest user
SELECT MIN(created_at) FROM users;

Real Testing Scenario:
Q: Find largest transaction of the day
A: 
SELECT MAX(amount) AS highest_transaction 
FROM transactions 
WHERE transaction_date = '2026-01-15';
```

### Using Multiple Aggregates

```
Example:
-- Complete sales summary
SELECT 
    COUNT(*) AS total_orders,
    SUM(amount) AS total_sales,
    AVG(amount) AS avg_order_value,
    MIN(amount) AS min_order,
    MAX(amount) AS max_order
FROM orders
WHERE order_date BETWEEN '2026-01-01' AND '2026-01-31';

Result:
┌──────────────┬──────────────┬─────────────────┬─────────────┬─────────────┐
│ total_orders │ total_sales  │ avg_order_value │ min_order   │ max_order   │
├──────────────┼──────────────┼─────────────────┼─────────────┼─────────────┤
│ 1500         │ 7500000      │ 5000            │ 100         │ 50000       │
└──────────────┴──────────────┴─────────────────┴─────────────┴─────────────┘
```

---

## 📋 GROUP BY & HAVING {#groupby}

### GROUP BY Clause

```
Purpose: Results ko groups mein organize karna

Syntax:
SELECT column, AGGREGATE_FUNCTION(column)
FROM table
GROUP BY column;

Examples:
-- Count users by city
SELECT city, COUNT(*) AS user_count
FROM users
GROUP BY city;

-- Total sales by product
SELECT product_id, SUM(amount) AS total_sales
FROM order_items
GROUP BY product_id;

-- Orders by status
SELECT status, COUNT(*) AS order_count
FROM orders
GROUP BY status;

Result Example:
┌───────────┬────────────┐
│ city      │ user_count │
├───────────┼────────────┤
│ Delhi     │ 150        │
│ Mumbai    │ 200        │
│ Bangalore │ 175        │
└───────────┴────────────┘
```

### GROUP BY with Multiple Columns

```
Example:
-- Orders by status and year
SELECT 
    status, 
    YEAR(order_date) AS order_year,
    COUNT(*) AS order_count
FROM orders
GROUP BY status, YEAR(order_date);

-- Sales by product and month
SELECT 
    product_id,
    MONTH(order_date) AS order_month,
    SUM(amount) AS total_sales
FROM order_items
GROUP BY product_id, MONTH(order_date);
```

### HAVING Clause

```
Purpose: Groups ko filter karna (WHERE aggregates ke sath use nahi ho sakta)

Syntax:
SELECT column, AGGREGATE_FUNCTION(column)
FROM table
GROUP BY column
HAVING condition;

Examples:
-- Cities with more than 100 users
SELECT city, COUNT(*) AS user_count
FROM users
GROUP BY city
HAVING COUNT(*) > 100;

-- Products with sales > 10000
SELECT product_id, SUM(amount) AS total_sales
FROM order_items
GROUP BY product_id
HAVING SUM(amount) > 10000;

-- Users with more than 5 orders
SELECT user_id, COUNT(*) AS order_count
FROM orders
GROUP BY user_id
HAVING COUNT(*) > 5;

Real Testing Scenario:
Q: Find duplicate emails in system
A: 
SELECT email, COUNT(*) AS count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

### WHERE vs HAVING

```
Key Difference:

WHERE:
- Rows ko filter karta hai BEFORE grouping
- Aggregates ke sath use nahi ho sakta

HAVING:
- Groups ko filter karta hai AFTER grouping
- Aggregates ke sath use ho sakta hai

Example:
-- Get active users, grouped by city, only cities with 50+ users
SELECT city, COUNT(*) AS user_count
FROM users
WHERE status = 'active'      -- Filter rows first
GROUP BY city                -- Then group
HAVING COUNT(*) >= 50;       -- Filter groups
```

---

## 🔁 Subqueries {#subqueries}

### What is a Subquery?

Query ke andar another query - nested query.

### Subquery in WHERE Clause

```
Example 1: Find users who have placed orders
SELECT * FROM users
WHERE id IN (
    SELECT DISTINCT user_id FROM orders
);

Example 2: Find users with orders above average
SELECT * FROM users
WHERE id IN (
    SELECT user_id FROM orders
    WHERE amount > (SELECT AVG(amount) FROM orders)
);

Example 3: Find products never ordered
SELECT * FROM products
WHERE id NOT IN (
    SELECT DISTINCT product_id FROM order_items
);
```

### Subquery in SELECT Clause

```
Example: Get users with their total order count
SELECT 
    u.name,
    u.email,
    (SELECT COUNT(*) FROM orders WHERE user_id = u.id) AS total_orders
FROM users u;

Result:
┌───────┬─────────────────┬──────────────┐
│ name  │ email           │ total_orders │
├───────┼─────────────────┼──────────────┤
│ John  │ john@test.com   │ 5            │
│ Jane  │ jane@test.com   │ 3            │
│ Bob   │ bob@test.com    │ 0            │
└───────┴─────────────────┴──────────────┘
```

### Subquery in FROM Clause

```
Example: Get average order value per user, then find top spenders
SELECT user_id, avg_order_value
FROM (
    SELECT user_id, AVG(amount) AS avg_order_value
    FROM orders
    GROUP BY user_id
) AS user_averages
WHERE avg_order_value > 5000;
```

### Correlated Subquery

```
Definition: Outer query ke row par depend karta hai

Example: Find users who have spent more than average
SELECT name, email
FROM users u
WHERE (
    SELECT SUM(amount) FROM orders WHERE user_id = u.id
) > (
    SELECT AVG(total_spent) FROM (
        SELECT user_id, SUM(amount) AS total_spent
        FROM orders
        GROUP BY user_id
    ) AS user_totals
);

Real Testing Scenario:
Q: Find customers who haven't ordered in last 6 months
A: 
SELECT name, email, last_order_date
FROM customers c
WHERE last_order_date < (
    SELECT DATE_SUB(MAX(order_date), INTERVAL 6 MONTH)
    FROM orders
);
```

---

## ✅ Data Validation Testing {#validation}

### Why Data Validation is Critical?

```
Common Data Issues Found in Testing:

❌ Data truncation (long values cut off)
❌ Wrong data type storage
❌ NULL values where NOT NULL expected
❌ Duplicate records
❌ Referential integrity violations
❌ Calculation errors
❌ Date/time format issues
❌ Special character handling
```

### Data Validation Checklist

```
┌─────────────────────────────────────────────────┐
│ DATA VALIDATION CHECKLIST                       │
├─────────────────────────────────────────────────┤
□ Field length validation                        │
□ Data type validation                            │
□ NULL/NOT NULL validation                        │
□ Default value validation                        │
□ Unique constraint validation                    │
□ Foreign key validation                          │
□ Check constraint validation                     │
□ Data format validation (date, email, phone)    │
□ Calculation accuracy                            │
□ Aggregation accuracy                            │
└─────────────────────────────────────────────────┘
```

### Field Length Validation

```
Scenario: Verify name field accepts exactly 100 characters

Test Steps:
1. Insert 100 character name
   INSERT INTO users (name) VALUES ('A...[100 chars]');
   Expected: Success

2. Insert 101 character name
   INSERT INTO users (name) VALUES ('A...[101 chars]');
   Expected: Error (data too long)

3. Verify stored data
   SELECT name, LENGTH(name) FROM users WHERE id = 1;
   Expected: Length = 100 (or error if exceeded)
```

### Data Type Validation

```
Scenario: Verify price field stores decimal correctly

Test Steps:
1. Insert decimal value
   INSERT INTO products (price) VALUES (99.99);
   Expected: Success

2. Insert string value
   INSERT INTO products (price) VALUES ('abc');
   Expected: Error (wrong data type)

3. Insert negative value (if not allowed)
   INSERT INTO products (price) VALUES (-10);
   Expected: Error (if CHECK constraint exists)

4. Verify storage
   SELECT price, TYPE(price) FROM products;
```

### NULL/NOT NULL Validation

```
Scenario: Verify email field is NOT NULL

Test Steps:
1. Insert without email
   INSERT INTO users (name) VALUES ('John');
   Expected: Error (NOT NULL constraint)

2. Insert with NULL email
   INSERT INTO users (name, email) VALUES ('John', NULL);
   Expected: Error

3. Insert with empty string
   INSERT INTO users (name, email) VALUES ('John', '');
   Expected: Success (empty string != NULL)

4. Verify NOT NULL columns
   SELECT column_name, is_nullable 
   FROM information_schema.columns 
   WHERE table_name = 'users';
```

### Unique Constraint Validation

```
Scenario: Verify email must be unique

Test Steps:
1. Insert first user
   INSERT INTO users (name, email) VALUES ('John', 'john@test.com');
   Expected: Success

2. Insert duplicate email
   INSERT INTO users (name, email) VALUES ('Jane', 'john@test.com');
   Expected: Error (unique constraint violation)

3. Verify duplicates
   SELECT email, COUNT(*) AS count
   FROM users
   GROUP BY email
   HAVING COUNT(*) > 1;
   
   Expected: No rows (no duplicates)
```

### Foreign Key Validation

```
Scenario: Verify order must have valid user

Test Setup:
CREATE TABLE users (
    id INT PRIMARY KEY,
    name VARCHAR(100)
);

CREATE TABLE orders (
    id INT PRIMARY KEY,
    user_id INT,
    amount DECIMAL,
    FOREIGN KEY (user_id) REFERENCES users(id)
);

Test Steps:
1. Insert order with valid user
   INSERT INTO orders (user_id, amount) VALUES (1, 100);
   Expected: Success

2. Insert order with invalid user
   INSERT INTO orders (user_id, amount) VALUES (999, 100);
   Expected: Error (foreign key violation)

3. Find orphaned records
   SELECT o.* FROM orders o
   LEFT JOIN users u ON o.user_id = u.id
   WHERE u.id IS NULL;
   
   Expected: No rows (no orphaned records)
```

### Date/Time Format Validation

```
Scenario: Verify date stored correctly

Test Steps:
1. Insert different date formats
   INSERT INTO orders (order_date) VALUES ('2026-01-15');
   INSERT INTO orders (order_date) VALUES ('2026-01-15 10:30:00');
   
2. Verify storage
   SELECT order_date, DATE_FORMAT(order_date, '%Y-%m-%d %H:%i:%s') 
   FROM orders;

3. Verify timezone handling (if applicable)
   SELECT 
       order_date,
       CONVERT_TZ(order_date, '+00:00', '+05:30') AS ist_time
   FROM orders;
```

### Calculation Accuracy Validation

```
Scenario: Verify order total calculation

Test Query:
SELECT 
    o.id AS order_id,
    SUM(oi.quantity * oi.price) AS calculated_total,
    o.stored_total,
    CASE 
        WHEN SUM(oi.quantity * oi.price) = o.stored_total 
        THEN 'MATCH' 
        ELSE 'MISMATCH' 
    END AS validation_status
FROM orders o
JOIN order_items oi ON o.id = oi.order_id
GROUP BY o.id, o.stored_total;

Expected: All rows show 'MATCH'
```

---

## 🧪 Database Testing Scenarios {#scenarios}

### Scenario 1: User Registration Data Validation

```
Test Objective:
Verify user registration data is stored correctly in database.

Preconditions:
- Users table exists with proper structure
- Test environment ready

Test Steps:

Step 1: Register new user via UI/API
   Input:
   - Name: John Doe
   - Email: john@example.com
   - Phone: 9876543210
   - Password: [hashed]

Step 2: Verify record in database
   Query:
   SELECT * FROM users WHERE email = 'john@example.com';
   
   Verify:
   ✓ Record exists
   ✓ Name matches
   ✓ Email matches
   ✓ Phone matches
   ✓ Password is hashed
   ✓ Created_at timestamp is current
   ✓ Status is 'active'

Step 3: Verify no duplicate
   Query:
   SELECT email, COUNT(*) FROM users 
   WHERE email = 'john@example.com'
   GROUP BY email;
   
   Expected: Count = 1

Step 4: Verify audit fields
   Query:
   SELECT created_at, created_by, updated_at 
   FROM users 
   WHERE email = 'john@example.com';
   
   Verify:
   ✓ Created_at is not NULL
   ✓ Updated_at = Created_at (for new record)
```

### Scenario 2: Order Processing Validation

```
Test Objective:
Verify order processing updates all related tables correctly.

Test Flow:
Order Placed → Payment Processing → Order Shipped → Order Delivered

Database Tables:
- orders (order header)
- order_items (order line items)
- payments (payment records)
- inventory (stock levels)
- shipments (shipping details)

Validation Queries:

1. After Order Placed:
   -- Verify order created
   SELECT * FROM orders WHERE order_id = 'ORD123';
   
   -- Verify order items created
   SELECT * FROM order_items WHERE order_id = 'ORD123';
   
   -- Verify inventory reduced
   SELECT product_id, stock_quantity 
   FROM inventory 
   WHERE product_id IN (SELECT product_id FROM order_items WHERE order_id = 'ORD123');

2. After Payment Success:
   -- Verify payment record
   SELECT * FROM payments WHERE order_id = 'ORD123';
   
   -- Verify order status updated
   SELECT status FROM orders WHERE order_id = 'ORD123';
   Expected: 'paid' or 'processing'

3. After Order Shipped:
   -- Verify shipment record
   SELECT * FROM shipments WHERE order_id = 'ORD123';
   
   -- Verify order status
   SELECT status FROM orders WHERE order_id = 'ORD123';
   Expected: 'shipped'

4. After Order Delivered:
   -- Verify final status
   SELECT status FROM orders WHERE order_id = 'ORD123';
   Expected: 'delivered'
   
   -- Verify delivery timestamp
   SELECT delivered_at FROM orders WHERE order_id = 'ORD123';
   Expected: Not NULL
```

### Scenario 3: Data Migration Validation

```
Test Objective:
Verify data migrated correctly from old system to new system.

Migration Scenario:
Old DB (legacy_db) → New DB (new_db)

Validation Approach:

1. Record Count Validation:
   -- Old database
   SELECT COUNT(*) FROM legacy_db.users;
   
   -- New database
   SELECT COUNT(*) FROM new_db.users;
   
   Expected: Both counts match

2. Data Comparison:
   -- Compare specific records
   SELECT 
       old.id,
       old.name AS old_name,
       new.name AS new_name,
       CASE WHEN old.name = new.name THEN 'MATCH' ELSE 'MISMATCH' END
   FROM legacy_db.users old
   JOIN new_db.users new ON old.id = new.id;

3. Data Transformation Validation:
   -- If data was transformed (e.g., name case change)
   SELECT 
       old.name AS old_name,
       new.name AS new_name,
       CASE 
           WHEN UPPER(old.name) = UPPER(new.name) THEN 'MATCH' 
           ELSE 'MISMATCH' 
       END
   FROM legacy_db.users old
   JOIN new_db.users new ON old.id = new.id;

4. Null Handling Validation:
   -- Check NULL values handled correctly
   SELECT 
       COUNT(*) AS total_records,
       SUM(CASE WHEN new.email IS NULL THEN 1 ELSE 0 END) AS null_emails
   FROM legacy_db.users old
   LEFT JOIN new_db.users new ON old.id = new.id;

5. Referential Integrity:
   -- Verify foreign keys migrated correctly
   SELECT 
       COUNT(*) AS orphaned_orders
   FROM new_db.orders o
   LEFT JOIN new_db.users u ON o.user_id = u.id
   WHERE u.id IS NULL;
   
   Expected: 0
```

### Scenario 4: ETL Testing

```
Test Objective:
Verify ETL process correctly extracts, transforms, and loads data.

ETL Flow:
Source Systems → Staging → Data Warehouse → Data Marts

Validation Queries:

1. Source to Staging Validation:
   -- Compare counts
   SELECT 
       (SELECT COUNT(*) FROM source.sales) AS source_count,
       (SELECT COUNT(*) FROM staging.sales) AS staging_count;

2. Transformation Validation:
   -- Verify calculations
   SELECT 
       s.product_id,
       s.quantity,
       s.price,
       s.quantity * s.price AS calculated_amount,
       s.total_amount AS stored_amount,
       CASE 
           WHEN s.quantity * s.price = s.total_amount 
           THEN 'CORRECT' 
           ELSE 'INCORRECT' 
       END AS validation
   FROM staging.sales s;

3. Data Quality Checks:
   -- Check for NULLs in critical fields
   SELECT 
       SUM(CASE WHEN product_id IS NULL THEN 1 ELSE 0 END) AS null_products,
       SUM(CASE WHEN quantity IS NULL THEN 1 ELSE 0 END) AS null_quantity,
       SUM(CASE WHEN amount IS NULL THEN 1 ELSE 0 END) AS null_amount
   FROM warehouse.fact_sales;
   
   Expected: All zeros

4. Aggregation Validation:
   -- Verify daily totals
   SELECT 
       sale_date,
       SUM(amount) AS daily_total,
       LAG(SUM(amount)) OVER (ORDER BY sale_date) AS prev_day_total
   FROM warehouse.fact_sales
   GROUP BY sale_date;

5. Dimensional Consistency:
   -- Verify foreign keys to dimensions
   SELECT 
       COUNT(*) AS orphaned_records
   FROM warehouse.fact_sales f
   LEFT JOIN warehouse.dim_date d ON f.date_id = d.date_id
   WHERE d.date_id IS NULL;
   
   Expected: 0
```

---

## 📦 SQL for Test Data Management {#testdata}

### Creating Test Data

```
Scenario: Create test data for e-commerce testing

-- Create test users
INSERT INTO users (name, email, phone, status) VALUES
('Test User 1', 'test1@test.com', '9876543211', 'active'),
('Test User 2', 'test2@test.com', '9876543212', 'active'),
('Test User 3', 'test3@test.com', '9876543213', 'inactive');

-- Create test products
INSERT INTO products (name, price, stock, status) VALUES
('Product A', 100.00, 50, 'active'),
('Product B', 200.00, 30, 'active'),
('Product C', 150.00, 0, 'out_of_stock');

-- Create test orders
INSERT INTO orders (user_id, total_amount, status, order_date) VALUES
(1, 300.00, 'delivered', '2026-01-01'),
(1, 500.00, 'shipped', '2026-01-10'),
(2, 200.00, 'processing', '2026-01-15');

-- Create test order items
INSERT INTO order_items (order_id, product_id, quantity, price) VALUES
(1, 1, 2, 100.00),
(1, 2, 1, 200.00),
(2, 2, 2, 200.00),
(2, 3, 1, 150.00),
(3, 2, 1, 200.00);
```

### Resetting Test Environment

```
Scenario: Reset test data before test execution

-- Delete test data (in correct order due to foreign keys)
DELETE FROM order_items WHERE order_id IN (SELECT id FROM orders WHERE user_id IN (1, 2, 3));
DELETE FROM payments WHERE order_id IN (SELECT id FROM orders WHERE user_id IN (1, 2, 3));
DELETE FROM shipments WHERE order_id IN (SELECT id FROM orders WHERE user_id IN (1, 2, 3));
DELETE FROM orders WHERE user_id IN (1, 2, 3);
DELETE FROM users WHERE id IN (1, 2, 3);
DELETE FROM products WHERE name IN ('Product A', 'Product B', 'Product C');

-- Reset auto-increment counters (if needed)
ALTER TABLE users AUTO_INCREMENT = 1;
ALTER TABLE orders AUTO_INCREMENT = 1;
ALTER TABLE products AUTO_INCREMENT = 1;

-- Verify cleanup
SELECT 
    (SELECT COUNT(*) FROM users WHERE id IN (1,2,3)) AS users_left,
    (SELECT COUNT(*) FROM orders WHERE user_id IN (1,2,3)) AS orders_left,
    (SELECT COUNT(*) FROM products WHERE name IN ('Product A','Product B','Product C')) AS products_left;
    
Expected: All zeros
```

### Generating Specific Test Scenarios

```
Scenario 1: Create user with no orders
INSERT INTO users (name, email, status) 
VALUES ('No Order User', 'noorder@test.com', 'active');

Scenario 2: Create user with many orders
-- First create user
INSERT INTO users (name, email, status) 
VALUES ('Power User', 'poweruser@test.com', 'active');
SET @user_id = LAST_INSERT_ID();

-- Then create 10 orders for this user
INSERT INTO orders (user_id, total_amount, status, order_date)
SELECT 
    @user_id,
    100 + (id * 10),
    'delivered',
    DATE_SUB(NOW(), INTERVAL id DAY)
FROM (SELECT 1 AS id UNION SELECT 2 UNION SELECT 3 UNION SELECT 4 UNION SELECT 5
      UNION SELECT 6 UNION SELECT 7 UNION SELECT 8 UNION SELECT 9 UNION SELECT 10) AS numbers;

Scenario 3: Create orders with specific status distribution
-- 50% delivered, 30% shipped, 20% processing
INSERT INTO orders (user_id, total_amount, status)
SELECT 
    1 AS user_id,
    100 AS amount,
    CASE 
        WHEN id <= 50 THEN 'delivered'
        WHEN id <= 80 THEN 'shipped'
        ELSE 'processing'
    END AS status
FROM (
    SELECT 1 AS id UNION SELECT 2 UNION ... UNION SELECT 100
) AS numbers;
```

### Data Setup for Edge Cases

```
Scenario: Create edge case test data

-- Empty/NULL values
INSERT INTO users (name, email, phone) 
VALUES ('Null Test', NULL, NULL);

-- Maximum length values
INSERT INTO users (name, email) 
VALUES ('A...[100 characters]', 'B...[100 characters]@test.com');

-- Special characters
INSERT INTO users (name, email) 
VALUES ('O''Brien & Co', 'test+special@test.com');

-- Unicode characters
INSERT INTO users (name, email) 
VALUES ('テスト 用户', 'unicode@test.com');

-- Duplicate values (if constraints allow)
INSERT INTO users (name, email, status) 
VALUES ('Duplicate', 'dup@test.com', 'active'),
       ('Duplicate', 'dup@test.com', 'pending');

-- Boundary values for dates
INSERT INTO orders (user_id, order_date, status) 
VALUES 
    (1, '1970-01-01', 'cancelled'),  -- Unix epoch
    (1, '2099-12-31', 'pending'),    -- Far future
    (1, '2026-02-29', 'cancelled');  -- Invalid date (should fail if 2026 is not leap year)
```

---

## 🎬 Real Testing Scenarios {#real}

### Scenario 1: E-commerce - Find Duplicate Orders

```
Business Problem:
Customers complaining about duplicate orders being charged.

Investigation Query:

-- Find potential duplicate orders
SELECT 
    user_id,
    total_amount,
    order_date,
    status,
    COUNT(*) AS duplicate_count
FROM orders
WHERE order_date >= DATE_SUB(NOW(), INTERVAL 30 DAY)
GROUP BY user_id, total_amount, order_date, status
HAVING COUNT(*) > 1
ORDER BY duplicate_count DESC;

-- Get detailed duplicate information
SELECT 
    o1.order_id AS order1,
    o2.order_id AS order2,
    o1.user_id,
    o1.total_amount,
    o1.order_date,
    o1.status,
    o2.status AS status2
FROM orders o1
JOIN orders o2 ON o1.user_id = o2.user_id 
    AND o1.total_amount = o2.total_amount
    AND o1.order_date = o2.order_date
    AND o1.order_id < o2.order_id
WHERE o1.order_date >= DATE_SUB(NOW(), INTERVAL 30 DAY);

Root Cause Analysis:
- Check if payment webhook called twice
- Check for retry logic issues
- Check for race conditions
```

### Scenario 2: Banking - Transaction Reconciliation

```
Business Problem:
Daily transaction totals don't match with bank statement.

Reconciliation Query:

-- System transaction total
SELECT 
    transaction_type,
    COUNT(*) AS transaction_count,
    SUM(amount) AS system_total
FROM transactions
WHERE transaction_date = '2026-01-15'
GROUP BY transaction_type;

-- Compare with bank feed
SELECT 
    t.transaction_type,
    COUNT(*) AS sys_count,
    SUM(t.amount) AS sys_amount,
    COUNT(b.transaction_id) AS bank_count,
    SUM(b.amount) AS bank_amount,
    SUM(t.amount) - SUM(b.amount) AS difference
FROM transactions t
LEFT JOIN bank_feed b ON t.reference_id = b.transaction_id
    AND t.amount = b.amount
WHERE t.transaction_date = '2026-01-15'
GROUP BY t.transaction_type
HAVING difference != 0;

-- Find unmatched transactions
SELECT 
    t.transaction_id,
    t.amount,
    t.reference_id,
    'IN SYSTEM NOT IN BANK' AS issue
FROM transactions t
LEFT JOIN bank_feed b ON t.reference_id = b.transaction_id
WHERE t.transaction_date = '2026-01-15'
  AND b.transaction_id IS NULL

UNION ALL

SELECT 
    b.transaction_id,
    b.amount,
    b.reference_id,
    'IN BANK NOT IN SYSTEM' AS issue
FROM bank_feed b
LEFT JOIN transactions t ON b.reference_id = t.reference_id
WHERE b.transaction_date = '2026-01-15'
  AND t.transaction_id IS NULL;
```

### Scenario 3: SaaS - Subscription Expiry Analysis

```
Business Problem:
Need to identify customers with expiring subscriptions for renewal campaign.

Analysis Query:

-- Subscriptions expiring in next 30 days
SELECT 
    c.customer_id,
    c.customer_name,
    c.email,
    s.subscription_id,
    s.plan_name,
    s.expiry_date,
    DATEDIFF(s.expiry_date, NOW()) AS days_until_expiry,
    s.amount
FROM customers c
JOIN subscriptions s ON c.customer_id = s.customer_id
WHERE s.status = 'active'
  AND s.expiry_date BETWEEN NOW() AND DATE_ADD(NOW(), INTERVAL 30 DAY)
ORDER BY days_until_expiry ASC;

-- Subscription revenue forecast
SELECT 
    DATE_FORMAT(expiry_date, '%Y-%m') AS expiry_month,
    COUNT(*) AS subscriptions_expiring,
    SUM(amount) AS revenue_at_risk
FROM subscriptions
WHERE status = 'active'
  AND expiry_date >= NOW()
GROUP BY DATE_FORMAT(expiry_date, '%Y-%m')
ORDER BY expiry_month;

-- Churn analysis
SELECT 
    DATE_FORMAT(cancellation_date, '%Y-%m') AS cancellation_month,
    COUNT(*) AS cancelled_subscriptions,
    SUM(CASE WHEN cancellation_reason = 'price' THEN 1 ELSE 0 END) AS price_churn,
    SUM(CASE WHEN cancellation_reason = 'features' THEN 1 ELSE 0 END) AS feature_churn,
    SUM(CASE WHEN cancellation_reason = 'support' THEN 1 ELSE 0 END) AS support_churn
FROM subscriptions
WHERE status = 'cancelled'
  AND cancellation_date >= DATE_SUB(NOW(), INTERVAL 6 MONTH)
GROUP BY DATE_FORMAT(cancellation_date, '%Y-%m');
```

### Scenario 4: Healthcare - Patient Data Privacy Audit

```
Business Problem:
Audit who accessed patient records for compliance.

Audit Query:

-- Access log analysis
SELECT 
    u.username,
    u.role,
    COUNT(*) AS access_count,
    COUNT(DISTINCT a.patient_id) AS unique_patients,
    DATE(a.access_time) AS access_date
FROM access_logs a
JOIN users u ON a.user_id = u.user_id
WHERE a.access_time >= DATE_SUB(NOW(), INTERVAL 30 DAY)
GROUP BY u.username, u.role, DATE(a.access_time)
ORDER BY access_count DESC;

-- Suspicious access patterns
SELECT 
    u.username,
    u.role,
    COUNT(*) AS after_hours_access,
    GROUP_CONCAT(DISTINCT a.patient_id) AS patient_ids_accessed
FROM access_logs a
JOIN users u ON a.user_id = u.user_id
WHERE (
    HOUR(a.access_time) < 8 
    OR HOUR(a.access_time) > 20
)
AND a.access_time >= DATE_SUB(NOW(), INTERVAL 7 DAY)
GROUP BY u.username, u.role
HAVING after_hours_access > 5;

-- Patients accessed by unauthorized users
SELECT 
    p.patient_id,
    p.patient_name,
    u.username,
    u.role,
    a.access_time
FROM access_logs a
JOIN users u ON a.user_id = u.user_id
JOIN patients p ON a.patient_id = p.patient_id
LEFT JOIN care_team ct ON p.patient_id = ct.patient_id 
    AND u.user_id = ct.user_id
WHERE ct.user_id IS NULL  -- Not in care team
  AND a.access_time >= DATE_SUB(NOW(), INTERVAL 30 DAY)
ORDER BY a.access_time DESC;
```

---

## 📝 SQL Test Cases {#test-cases}

### Test Case 1: User Registration Data Validation

```
Test Case ID: TC_SQL_001
Test Case Name: Verify User Registration Data Storage
Test Type: Database Validation
Priority: HIGH

Objective:
Verify user registration data is correctly stored in database

Preconditions:
- Database connection available
- Test environment ready
- No existing user with test email

Test Steps:

| Step | Action | SQL Query | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Register user via UI | - | Registration successful |
| 2 | Query database | SELECT * FROM users WHERE email = 'test@test.com'; | Record exists |
| 3 | Verify name | SELECT name FROM users WHERE email = 'test@test.com'; | Name matches |
| 4 | Verify email | SELECT email FROM users WHERE email = 'test@test.com'; | Email matches |
| 5 | Verify password hashed | SELECT password FROM users WHERE email = 'test@test.com'; | Password is hashed |
| 6 | Verify timestamp | SELECT created_at FROM users WHERE email = 'test@test.com'; | Timestamp is current |
| 7 | Verify status | SELECT status FROM users WHERE email = 'test@test.com'; | Status = 'active' |
| 8 | Check for duplicates | SELECT email, COUNT(*) FROM users WHERE email = 'test@test.com' GROUP BY email; | Count = 1 |

Pass Criteria:
✓ All fields stored correctly
✓ Password is hashed (not plain text)
✓ Timestamps are accurate
✓ No duplicate records
```

### Test Case 2: Order Total Calculation Validation

```
Test Case ID: TC_SQL_002
Test Case Name: Verify Order Total Calculation
Test Type: Data Validation
Priority: CRITICAL

Objective:
Verify order total is correctly calculated from line items

Preconditions:
- Order with multiple items exists
- Order ID: ORD12345

Test Steps:

| Step | Action | SQL Query | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Get order total | SELECT total_amount FROM orders WHERE order_id = 'ORD12345'; | Stored total |
| 2 | Calculate from items | SELECT SUM(quantity * price) FROM order_items WHERE order_id = 'ORD12345'; | Calculated total |
| 3 | Compare | (Combine above queries) | Stored = Calculated |
| 4 | Verify tax | SELECT tax_amount FROM orders WHERE order_id = 'ORD12345'; | Tax matches calculation |
| 5 | Verify shipping | SELECT shipping_amount FROM orders WHERE order_id = 'ORD12345'; | Shipping matches policy |
| 6 | Verify grand total | SELECT grand_total FROM orders WHERE order_id = 'ORD12345'; | Sum of all components |

Validation Query:
SELECT 
    o.order_id,
    o.total_amount AS stored_total,
    SUM(oi.quantity * oi.price) AS calculated_total,
    o.tax_amount,
    o.shipping_amount,
    o.grand_total,
    CASE 
        WHEN o.total_amount = SUM(oi.quantity * oi.price) 
        THEN 'PASS' 
        ELSE 'FAIL' 
    END AS result
FROM orders o
JOIN order_items oi ON o.order_id = oi.order_id
WHERE o.order_id = 'ORD12345'
GROUP BY o.order_id, o.total_amount, o.tax_amount, o.shipping_amount, o.grand_total;

Pass Criteria:
✓ Stored total matches calculated total
✓ Tax calculation is correct
✓ Shipping calculation is correct
✓ Grand total is sum of all components
```

### Test Case 3: Referential Integrity Validation

```
Test Case ID: TC_SQL_003
Test Case Name: Verify Referential Integrity
Test Type: Data Integrity
Priority: HIGH

Objective:
Verify all foreign key relationships are maintained

Test Areas:
- Orders must have valid users
- Order items must have valid orders and products
- Payments must have valid orders

Test Queries:

-- Check for orphaned orders
SELECT COUNT(*) AS orphaned_orders
FROM orders o
LEFT JOIN users u ON o.user_id = u.id
WHERE u.id IS NULL;
Expected: 0

-- Check for orphaned order items
SELECT COUNT(*) AS orphaned_items
FROM order_items oi
LEFT JOIN orders o ON oi.order_id = o.id
WHERE o.id IS NULL;
Expected: 0

-- Check for invalid product references
SELECT COUNT(*) AS invalid_products
FROM order_items oi
LEFT JOIN products p ON oi.product_id = p.id
WHERE p.id IS NULL;
Expected: 0

-- Check for orphaned payments
SELECT COUNT(*) AS orphaned_payments
FROM payments p
LEFT JOIN orders o ON p.order_id = o.id
WHERE o.id IS NULL;
Expected: 0

Pass Criteria:
✓ No orphaned orders
✓ No orphaned order items
✓ No invalid product references
✓ No orphaned payments
✓ All foreign key relationships valid
```

### Test Case 4: Data Migration Validation

```
Test Case ID: TC_SQL_004
Test Case Name: Verify Data Migration Completeness
Test Type: Migration Testing
Priority: CRITICAL

Objective:
Verify all data migrated correctly from old to new system

Preconditions:
- Old database accessible
- New database populated
- Migration completed

Test Steps:

| Step | Validation | Query | Expected |
|------|------------|-------|----------|
| 1 | User count | SELECT COUNT(*) FROM users; | Old = New |
| 2 | Product count | SELECT COUNT(*) FROM products; | Old = New |
| 3 | Order count | SELECT COUNT(*) FROM orders; | Old = New |
| 4 | Data comparison | JOIN old and new tables | All fields match |
| 5 | NULL handling | Check NULL values | Properly migrated |
| 6 | Data transformation | Verify transformations | Correctly applied |

Detailed Validation Query:
SELECT 
    'Users' AS table_name,
    (SELECT COUNT(*) FROM old_db.users) AS old_count,
    (SELECT COUNT(*) FROM new_db.users) AS new_count,
    CASE 
        WHEN (SELECT COUNT(*) FROM old_db.users) = 
             (SELECT COUNT(*) FROM new_db.users) 
        THEN 'PASS' 
        ELSE 'FAIL' 
    END AS result
UNION ALL
SELECT 
    'Products',
    (SELECT COUNT(*) FROM old_db.products),
    (SELECT COUNT(*) FROM new_db.products),
    CASE 
        WHEN (SELECT COUNT(*) FROM old_db.products) = 
             (SELECT COUNT(*) FROM new_db.products) 
        THEN 'PASS' 
        ELSE 'FAIL' 
    END
UNION ALL
SELECT 
    'Orders',
    (SELECT COUNT(*) FROM old_db.orders),
    (SELECT COUNT(*) FROM new_db.orders),
    CASE 
        WHEN (SELECT COUNT(*) FROM old_db.orders) = 
             (SELECT COUNT(*) FROM new_db.orders) 
        THEN 'PASS' 
        ELSE 'FAIL' 
    END;

Pass Criteria:
✓ All record counts match
✓ Sample data comparison passes
✓ NULL values handled correctly
✓ Transformations applied correctly
✓ No data loss
```

### Test Case 5: Duplicate Data Detection

```
Test Case ID: TC_SQL_005
Test Case Name: Verify No Duplicate Records
Test Type: Data Quality
Priority: HIGH

Objective:
Verify no duplicate records exist in critical tables

Test Areas:
- Duplicate emails in users
- Duplicate order numbers
- Duplicate product SKUs

Test Queries:

-- Check duplicate emails
SELECT email, COUNT(*) AS count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
Expected: No rows

-- Check duplicate order numbers
SELECT order_number, COUNT(*) AS count
FROM orders
GROUP BY order_number
HAVING COUNT(*) > 1;
Expected: No rows

-- Check duplicate product SKUs
SELECT sku, COUNT(*) AS count
FROM products
GROUP BY sku
HAVING COUNT(*) > 1;
Expected: No rows

-- Summary query
SELECT 
    'Duplicate Emails' AS check_name,
    COUNT(*) AS duplicate_count
FROM (
    SELECT email FROM users GROUP BY email HAVING COUNT(*) > 1
) dup
UNION ALL
SELECT 
    'Duplicate Orders',
    COUNT(*)
FROM (
    SELECT order_number FROM orders GROUP BY order_number HAVING COUNT(*) > 1
) dup
UNION ALL
SELECT 
    'Duplicate SKUs',
    COUNT(*)
FROM (
    SELECT sku FROM products GROUP BY sku HAVING COUNT(*) > 1
) dup;

Expected: All counts = 0

Pass Criteria:
✓ No duplicate emails
✓ No duplicate order numbers
✓ No duplicate SKUs
✓ All unique constraints enforced
```

---

## 🎤 SQL Interview Questions for Testers {#interview}

### Q1: Why do testers need SQL knowledge?

**Answer:**

```
Testers need SQL for several critical activities:

1. Data Validation
   - Verify data saved correctly in database
   - Check calculations and aggregations
   - Validate data transformations

2. Backend Testing
   - API response validation against database
   - Business logic verification
   - Data integrity checks

3. Defect Investigation
   - Find root cause of issues
   - Analyze production problems
   - Reproduce data-related bugs

4. Test Data Management
   - Create test data directly
   - Reset test environment
   - Generate specific scenarios

5. Reporting
   - Extract test metrics
   - Analyze defect patterns
   - Create dashboards

Real Example from My Experience:
Found a critical bug where order totals were being calculated incorrectly.
UI showed correct total, but database had wrong value. SQL query revealed
the calculation was happening twice in some cases. This would have caused
revenue loss if not caught before production.

Key SQL Skills for Testers:
✓ SELECT queries with filtering
✓ JOINs for multi-table validation
✓ Aggregate functions for calculations
✓ GROUP BY for data analysis
✓ Subqueries for complex validation
```

### Q2: How do you verify data integrity in testing?

**Answer:**

```
My Data Integrity Validation Approach:

1. Referential Integrity Checks
   -- Check for orphaned records
   SELECT COUNT(*) FROM orders o
   LEFT JOIN users u ON o.user_id = u.id
   WHERE u.id IS NULL;
   Expected: 0

2. Unique Constraint Validation
   -- Check for duplicates
   SELECT email, COUNT(*) FROM users
   GROUP BY email HAVING COUNT(*) > 1;
   Expected: No rows

3. NOT NULL Validation
   -- Check critical fields are not NULL
   SELECT COUNT(*) FROM users
   WHERE email IS NULL OR name IS NULL;
   Expected: 0

4. Data Type Validation
   -- Check numeric fields contain valid numbers
   SELECT COUNT(*) FROM orders
   WHERE total_amount < 0;
   Expected: 0 (if negative not allowed)

5. Calculation Accuracy
   -- Verify calculated fields
   SELECT 
       o.total_amount,
       SUM(oi.quantity * oi.price) AS calculated,
       CASE WHEN o.total_amount = SUM(oi.quantity * oi.price)
            THEN 'PASS' ELSE 'FAIL' END
   FROM orders o
   JOIN order_items oi ON o.id = oi.order_id
   GROUP BY o.id;

6. Date/Time Validation
   -- Check date logic
   SELECT COUNT(*) FROM orders
   WHERE delivered_at < shipped_at
      OR shipped_at < order_date;
   Expected: 0

Example:
In my project, we had a data integrity issue where payments
were getting disconnected from orders after a migration. My
validation queries found 50+ orphaned payment records. We fixed
the migration script and re-ran, preventing production issues.
```

### Q3: Write a query to find the second highest salary

**Answer:**

```
Multiple Approaches:

Method 1: Using LIMIT/OFFSET (MySQL, PostgreSQL)
SELECT DISTINCT salary
FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;

Method 2: Using Subquery
SELECT MAX(salary) AS second_highest
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);

Method 3: Using DENSE_RANK (SQL Server, Oracle)
SELECT salary
FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rank
    FROM employees
) ranked
WHERE rank = 2;

Method 4: Using TOP (SQL Server)
SELECT TOP 1 salary
FROM (
    SELECT TOP 2 salary
    FROM employees
    ORDER BY salary DESC
) AS top2
ORDER BY salary ASC;

My Preferred Approach:
I use Method 1 (LIMIT/OFFSET) for MySQL/PostgreSQL as it's
simple and efficient. For interviews, I explain multiple
approaches to show depth of knowledge.

Edge Cases to Consider:
- What if there's only one salary? (Query returns NULL)
- What if multiple people have same second highest salary?
  (DISTINCT handles this)
- What if there are NULL salaries? (Add WHERE salary IS NOT NULL)
```

### Q4: How do you find duplicate records in a table?

**Answer:**

```
Finding Duplicates:

Method 1: Simple Duplicate Check
SELECT email, COUNT(*) AS count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;

Method 2: Show All Duplicate Records
SELECT u.*
FROM users u
JOIN (
    SELECT email
    FROM users
    GROUP BY email
    HAVING COUNT(*) > 1
) dup ON u.email = dup.email
ORDER BY u.email;

Method 3: Multiple Column Duplicates
SELECT name, email, COUNT(*) AS count
FROM users
GROUP BY name, email
HAVING COUNT(*) > 1;

Method 4: Find Duplicates with Row IDs
SELECT 
    u.id,
    u.name,
    u.email,
    ROW_NUMBER() OVER (PARTITION BY u.email ORDER BY u.id) AS rn
FROM users u
HAVING rn > 1;  -- Shows duplicate rows (keeps first)

Finding and Deleting Duplicates (Keep One):

-- MySQL
DELETE u1 FROM users u1
JOIN users u2 ON u1.email = u2.email
WHERE u1.id > u2.id;

-- SQL Server
WITH CTE AS (
    SELECT *, 
           ROW_NUMBER() OVER (PARTITION BY email ORDER BY id) AS rn
    FROM users
)
DELETE FROM CTE WHERE rn > 1;

Real Testing Scenario:
In data migration testing, I found 200+ duplicate customer records.
Used GROUP BY with HAVING to identify them, then worked with
business to determine which records to keep based on data quality.
```

### Q5: What is the difference between WHERE and HAVING?

**Answer:**

```
Key Differences:

WHERE:
- Filters rows BEFORE grouping
- Cannot use aggregate functions
- Applied first in query execution

HAVING:
- Filters groups AFTER grouping
- Can use aggregate functions
- Applied after GROUP BY

Example to Illustrate:

-- Get active users, grouped by city, only cities with 50+ users

SELECT city, COUNT(*) AS user_count
FROM users
WHERE status = 'active'      -- Filter individual rows first
GROUP BY city                -- Then group the filtered rows
HAVING COUNT(*) >= 50;       -- Filter groups based on aggregate

Execution Order:
1. WHERE status = 'active'   → Filters rows
2. GROUP BY city             → Groups filtered rows
3. HAVING COUNT(*) >= 50    → Filters groups
4. SELECT city, COUNT(*)    → Returns results

Common Mistake:
❌ SELECT city, COUNT(*) FROM users
   WHERE COUNT(*) > 50      -- WRONG: Can't use aggregate in WHERE
   GROUP BY city;

✓ Correct:
   SELECT city, COUNT(*) FROM users
   GROUP BY city
   HAVING COUNT(*) > 50;    -- RIGHT: Use HAVING for aggregates

Real Testing Scenario:
Q: Find customers with more than 10 orders in 2025

A: 
SELECT user_id, COUNT(*) AS order_count
FROM orders
WHERE order_date >= '2025-01-01'   -- Filter by date first
  AND order_date < '2026-01-01'
GROUP BY user_id
HAVING COUNT(*) > 10;              -- Filter by count after grouping
```

### Q6: Explain different types of JOINs with examples

**Answer:**

```
Types of JOINs:

1. INNER JOIN - Only matching rows
   SELECT u.name, o.order_id
   FROM users u
   INNER JOIN orders o ON u.id = o.user_id;
   
   Result: Only users who have orders

2. LEFT JOIN - All left + matching right
   SELECT u.name, o.order_id
   FROM users u
   LEFT JOIN orders o ON u.id = o.user_id;
   
   Result: All users, with orders where available (NULL if no orders)

3. RIGHT JOIN - All right + matching left
   SELECT u.name, o.order_id
   FROM users u
   RIGHT JOIN orders o ON u.id = o.user_id;
   
   Result: All orders, with user info where available

4. FULL OUTER JOIN - All rows from both
   SELECT u.name, o.order_id
   FROM users u
   FULL OUTER JOIN orders o ON u.id = o.user_id;
   
   Result: All users and all orders

5. CROSS JOIN - Cartesian product
   SELECT u.name, p.product_name
   FROM users u
   CROSS JOIN products p;
   
   Result: Every user paired with every product

6. SELF JOIN - Table joined with itself
   SELECT e.name AS employee, m.name AS manager
   FROM employees e
   LEFT JOIN employees m ON e.manager_id = m.id;

Real Testing Scenarios:

INNER JOIN: Get users with their orders
LEFT JOIN: Find users without orders (WHERE o.order_id IS NULL)
RIGHT JOIN: Find orphaned orders (WHERE u.id IS NULL)

Example Question I Solved:
"Find all customers who never placed an order"

SELECT u.name, u.email
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
WHERE o.order_id IS NULL;
```

### Q7: How do you test database performance?

**Answer:**

```
Database Performance Testing Approach:

1. Query Execution Time
   -- Check how long query takes
   SET PROFILING = 1;
   SELECT * FROM large_table WHERE condition;
   SHOW PROFILES;
   
   Expected: < 1 second for simple queries

2. EXPLAIN Plan Analysis
   EXPLAIN SELECT * FROM users WHERE email = 'test@test.com';
   
   Check:
   ✓ Using index? (type = 'ref' or 'range')
   ✓ Full table scan? (type = 'ALL' - bad for large tables)
   ✓ Rows examined vs rows returned

3. Index Usage Validation
   -- Without index (slow)
   SELECT * FROM orders WHERE user_id = 123;
   
   -- Create index
   CREATE INDEX idx_user_id ON orders(user_id);
   
   -- With index (fast)
   SELECT * FROM orders WHERE user_id = 123;

4. Load Testing
   -- Run query multiple times with concurrent connections
   -- Monitor response time degradation
   -- Check for deadlocks

5. Common Performance Issues I Look For:
   □ Missing indexes on WHERE/JOIN columns
   □ SELECT * instead of specific columns
   □ N+1 query problem
   □ Missing query caching
   □ Lock contention
   □ Inefficient subqueries

6. Optimization Techniques:
   ✓ Add appropriate indexes
   ✓ Optimize query structure
   ✓ Use appropriate JOINs
   ✓ Avoid correlated subqueries
   ✓ Implement query caching
   ✓ Partition large tables

Real Example:
Found a query taking 30 seconds in production. EXPLAIN showed
full table scan on 10M rows. Added index on filter column,
reduced time to 0.5 seconds. Simple but impactful fix!
```

---

## ✅ SQL Quick Reference

### Common SQL Commands for Testers

```
Data Retrieval:
SELECT * FROM table;
SELECT col1, col2 FROM table;
SELECT DISTINCT col FROM table;

Filtering:
WHERE col = value
WHERE col IN (val1, val2)
WHERE col BETWEEN val1 AND val2
WHERE col LIKE 'pattern%'
WHERE col IS NULL

Joining:
INNER JOIN table2 ON t1.col = t2.col
LEFT JOIN table2 ON t1.col = t2.col
RIGHT JOIN table2 ON t1.col = t2.col

Aggregation:
COUNT(*), SUM(col), AVG(col), MIN(col), MAX(col)
GROUP BY col
HAVING condition

Data Modification:
INSERT INTO table (col1, col2) VALUES (val1, val2)
UPDATE table SET col = val WHERE condition
DELETE FROM table WHERE condition
```

### Quick Validation Queries

```
Count Validation:
SELECT COUNT(*) FROM table;

Duplicate Check:
SELECT col, COUNT(*) FROM table GROUP BY col HAVING COUNT(*) > 1;

Null Check:
SELECT COUNT(*) FROM table WHERE col IS NULL;

Referential Integrity:
SELECT COUNT(*) FROM child c LEFT JOIN parent p ON c.parent_id = p.id WHERE p.id IS NULL;

Data Comparison:
SELECT old.col, new.col FROM old_table old JOIN new_table new ON old.id = new.id WHERE old.col != new.col;
```

---

## 📊 Summary

### Key Takeaways

```
✅ SQL is essential skill for testers
✅ SELECT, WHERE, JOIN are fundamental
✅ Aggregate functions for validation
✅ Subqueries for complex scenarios
✅ Data integrity is critical
✅ Practice writing queries regularly
✅ Understand database schema
✅ Use SQL for defect investigation
```

### Career Advice

```
📌 Practice SQL daily on sample databases
📌 Learn your organization's database schema
📌 Master JOINs and aggregate functions
📌 Understand EXPLAIN plans
📌 Learn database-specific features
📌 Practice data validation scenarios
📌 Get comfortable with complex queries
📌 Build sample databases for practice
```

---

*SQL for Testers Module*  
*For QA Professionals & Aspirants*  
*Language: Hinglish (Hindi + English)*  
*Created: 2026*

**Happy SQL Testing! 📊✅**
