# Module 08: Database Testing

## Database Testing Complete Guide - Manual Tester के लिए

**Last Updated:** January 2026  
**Reading Time:** 2.5 hours  
**Level:** Intermediate

---

## 📋 Table of Contents

1. [Database Basics for Testers](#database-basics)
2. [SQL Fundamentals](#sql-fundamentals)
3. [Data Validation Testing](#data-validation)
4. [ACID Properties Testing](#acid-properties)
5. [Database Integrity Testing](#integrity-testing)
6. [Query Optimization for Testers](#query-optimization)
7. [Real Database Testing Scenarios](#real-scenarios)
8. [Database Testing Tools](#database-tools)
9. [Best Practices & Common Issues](#best-practices)
10. [20+ Interview Questions](#interview-questions)

---

## <a name="database-basics"></a>Database Basics for Testers

### Database क्या है?

**Database = Structured data का collection**

```
Simple Example:

Excel Sheet जैसा सोचो:
┌─────────────────────────────────────────────────────────┐
│  ID  │  Name      │  Email              │  Age  │ City │
├─────────────────────────────────────────────────────────┤
│  1   │  John      │  john@mail.com      │  25   │ NYC  │
│  2   │  Jane      │  jane@mail.com      │  30   │ LA   │
│  3   │  Bob       │  bob@mail.com       │  35   │ SF   │
└─────────────────────────────────────────────────────────┘

ये Excel sheet को Database Table कहते हैं।
```

### Database Testing क्यों जरूरी है?

```
WITHOUT DATABASE TESTING:
✗ Wrong data save हो सकता है
✗ Data loss हो सकता है
✗ Data corruption हो सकता है
✗ Security issues रह सकते हैं
✗ Performance problems आ सकते हैं

WITH DATABASE TESTING:
✓ Data integrity maintain रहती है
✓ Data accuracy verify होती है
✓ Business rules enforce होती हैं
✓ Performance optimized रहती है
✓ Security vulnerabilities पकड़ में आते हैं
```

### Tester को Database क्यों समझना चाहिए?

```
REAL SCENARIOS:

1. FORM SUBMISSION
   Frontend: User ने form भरा
   Backend: Database में save हुआ
   Testing: दोनों जगह data match हो रहा है?

2. REPORT GENERATION
   Requirement: Sales report generate करो
   Source: Database से data आता है
   Testing: Report में data सही है?

3. DATA MIGRATION
   Old System → New System
   Testing: सारा data transfer हुआ? Corruption तो नहीं?

4. BUG INVESTIGATION
   UI में error दिख रहा है
   Root Cause: Database में wrong data
   Testing: Database query चलाकर verify करना
```

### Common Database Systems

```
┌────────────────────────────────────────────────────────────┐
│              POPULAR DATABASE SYSTEMS                      │
├────────────────────────────────────────────────────────────┤
│ Database      │ Type          │ Use Case                  │
├────────────────────────────────────────────────────────────┤
│ MySQL         │ Relational    │ Web apps, Small-medium    │
│ PostgreSQL    │ Relational    │ Complex queries, Enterprise│
│ Oracle        │ Relational    │ Large enterprise systems  │
│ SQL Server    │ Relational    │ Microsoft ecosystem       │
│ MongoDB       │ NoSQL         │ Unstructured data, JSON   │
│ SQLite        │ Embedded      │ Mobile apps, Local storage│
│ Redis         │ Key-Value     │ Caching, Session storage  │
└────────────────────────────────────────────────────────────┘
```

### Database Architecture (Simple)

```
┌────────────────────────────────────────────────────────────┐
│                 3-TIER ARCHITECTURE                        │
│                                                            │
│  ┌─────────────┐                                          │
│  │   USER      │  ← Tier 1: Presentation (UI)            │
│  │  (Browser)  │                                          │
│  └──────┬──────┘                                          │
│         │                                                  │
│         ▼                                                  │
│  ┌─────────────┐                                          │
│  │   SERVER    │  ← Tier 2: Application (Backend)        │
│  │  (API/Code) │                                          │
│  └──────┬──────┘                                          │
│         │                                                  │
│         ▼                                                  │
│  ┌─────────────┐                                          │
│  │  DATABASE   │  ← Tier 3: Data Storage                 │
│  │  (MySQL,    │                                          │
│  │   PG, etc.) │                                          │
│  └─────────────┘                                          │
└────────────────────────────────────────────────────────────┘

TESTER का काम: हर tier पर data verify करना
```

---

## <a name="sql-fundamentals"></a>SQL Fundamentals

### SQL क्या है?

**SQL = Structured Query Language**

```
Database से बात करने की language।

4 Main Categories:

1. DDL (Data Definition Language)
   └─ Database structure बनाने/बदलने के लिए
   └─ CREATE, ALTER, DROP, TRUNCATE

2. DML (Data Manipulation Language)
   └─ Data के साथ काम करने के लिए
   └─ INSERT, UPDATE, DELETE

3. DQL (Data Query Language)
   └─ Data retrieve करने के लिए
   └─ SELECT

4. DCL (Data Control Language)
   └─ Permissions control करने के लिए
   └─ GRANT, REVOKE
```

### Essential SQL Queries for Testers

#### 1. SELECT Query (Data retrieve करना)

```sql
-- Basic SELECT
SELECT * FROM users;
-- सभी columns और सभी rows लाएगा

SELECT id, name, email FROM users;
-- सिर्फ specified columns

SELECT * FROM users WHERE city = 'Delhi';
-- सिर्फ Delhi के users

SELECT * FROM users WHERE age > 25;
-- Age > 25 वाले users

SELECT * FROM users WHERE age >= 25 AND city = 'Mumbai';
-- Multiple conditions

SELECT * FROM users WHERE city = 'Delhi' OR city = 'Mumbai';
-- Delhi OR Mumbai के users

SELECT * FROM users WHERE email LIKE '%@gmail.com';
-- Gmail users (LIKE with wildcard)

SELECT * FROM users ORDER BY name ASC;
-- Alphabetical order में names

SELECT * FROM users ORDER BY created_at DESC;
-- Newest users first

SELECT * FROM users LIMIT 10;
-- सिर्फ 10 rows
```

#### 2. INSERT Query (New data add करना)

```sql
-- Single row insert
INSERT INTO users (name, email, age, city)
VALUES ('Rahul', 'rahul@test.com', 28, 'Delhi');

-- Multiple rows insert
INSERT INTO users (name, email, age, city)
VALUES 
    ('Priya', 'priya@test.com', 25, 'Mumbai'),
    ('Amit', 'amit@test.com', 30, 'Bangalore'),
    ('Sneha', 'sneha@test.com', 27, 'Pune');
```

#### 3. UPDATE Query (Existing data update करना)

```sql
-- Single row update
UPDATE users 
SET city = 'Chennai' 
WHERE id = 1;

-- Multiple columns update
UPDATE users 
SET city = 'Hyderabad', age = 29 
WHERE id = 2;

-- Bulk update with condition
UPDATE users 
SET status = 'active' 
WHERE last_login > '2026-01-01';

-- IMPORTANT: हमेशा WHERE clause use करो!
-- नहीं तो पूरी table update हो जाएगी!
```

#### 4. DELETE Query (Data delete करना)

```sql
-- Single row delete
DELETE FROM users WHERE id = 5;

-- Multiple rows with condition
DELETE FROM users WHERE status = 'inactive';

-- Delete all (DANGEROUS!)
DELETE FROM users;
-- या
TRUNCATE TABLE users;
-- TRUNCATE ज्यादा fast है और reset करता है
```

### WHERE Clause Operators

```
┌────────────────────────────────────────────────────────────┐
│                  SQL OPERATORS                             │
├────────────────────────────────────────────────────────────┤
│ Operator  │ Description         │ Example                 │
├────────────────────────────────────────────────────────────┤
│ =         │ Equal to            │ WHERE age = 25          │
│ != or <>  │ Not equal to        │ WHERE status != 'deleted'│
│ >         │ Greater than        │ WHERE age > 18          │
│ <         │ Less than           │ WHERE age < 60          │
│ >=        │ Greater or equal    │ WHERE age >= 18         │
│ <=        │ Less or equal       │ WHERE age <= 60         │
│ LIKE      │ Pattern match       │ WHERE name LIKE 'A%'    │
│ IN        │ Multiple values     │ WHERE city IN ('Delhi', 'Mumbai') │
│ BETWEEN   │ Range               │ WHERE age BETWEEN 20 AND 30 │
│ IS NULL   │ NULL check          │ WHERE phone IS NULL     │
│ IS NOT NULL│ NOT NULL check    │ WHERE email IS NOT NULL │
└────────────────────────────────────────────────────────────┘
```

### LIKE Pattern Examples

```sql
-- Name starts with 'A'
SELECT * FROM users WHERE name LIKE 'A%';

-- Name ends with 'h'
SELECT * FROM users WHERE name LIKE '%h';

-- Name contains 'oh'
SELECT * FROM users WHERE name LIKE '%oh%';

-- Email ends with @gmail.com
SELECT * FROM users WHERE email LIKE '%@gmail.com';

-- Phone starts with 98
SELECT * FROM users WHERE phone LIKE '98%';

-- Single character wildcard (any one character)
SELECT * FROM users WHERE name LIKE 'R_hul';
-- Matches: Rahul, Rohit, Ruhul
```

---

## <a name="sql-fundamentals"></a>JOIN Operations

### JOIN क्यों जरूरी है?

```
REAL SCENARIO:

E-commerce Database में multiple tables:
- users table (customer info)
- orders table (order details)
- products table (product details)

Question: "सभी orders के साथ customer name चाहिए"

Solution: JOIN का use करो!
```

### JOIN Types with Examples

```
TABLES:

users table:
┌────┬───────────┬───────────────┬──────────┐
│ id │ name      │ email         │ city     │
├────┼───────────┼───────────────┼──────────┤
│ 1  │ Rahul     │ rahul@test.com│ Delhi    │
│ 2  │ Priya     │ priya@test.com│ Mumbai   │
│ 3  │ Amit      │ amit@test.com│ Delhi    │
│ 4  │ Sneha     │ sneha@test.com│ Pune     │
└────┴───────────┴───────────────┴──────────┘

orders table:
┌─────┬────────────┬─────────┬──────────┐
│id   │ user_id    │ product │ amount   │
├─────┼────────────┼─────────┼──────────┤
│ 101 │ 1          │ Laptop  │ 50000    │
│ 102 │ 1          │ Mouse   │ 500      │
│ 103 │ 2          │ Keyboard│ 2000     │
│ 104 │ 5          │ Monitor │ 15000    │
│ 105 │ NULL       │ Headset │ 1000     │
└─────┴────────────┴─────────┴──────────┘
Note: user_id 5 users table में नहीं है
      user_id 3, 4 के orders नहीं हैं
```

#### 1. INNER JOIN (Common records only)

```sql
SELECT users.name, orders.product, orders.amount
FROM users
INNER JOIN orders ON users.id = orders.user_id;

RESULT:
┌───────────┬──────────┬────────┐
│ name      │ product  │ amount │
├───────────┼──────────┼────────┤
│ Rahul     │ Laptop   │ 50000  │
│ Rahul     │ Mouse    │ 500    │
│ Priya     │ Keyboard │ 2000   │
└───────────┴──────────┴────────┘

Note: 
- Amit और Sneha के orders नहीं हैं, इसलिए नहीं आए
- Order 104 (user_id 5) users table में नहीं है, इसलिए नहीं आया
```

#### 2. LEFT JOIN (All from left + matching from right)

```sql
SELECT users.name, orders.product
FROM users
LEFT JOIN orders ON users.id = orders.user_id;

RESULT:
┌───────────┬──────────┐
│ name      │ product  │
├───────────┼──────────┤
│ Rahul     │ Laptop   │
│ Rahul     │ Mouse    │
│ Priya     │ Keyboard │
│ Amit      │ NULL     │  ← No orders
│ Sneha     │ NULL     │  ← No orders
└───────────┴──────────┘

Note: सभी users आए, भले ही orders हों या न हों
```

#### 3. RIGHT JOIN (All from right + matching from left)

```sql
SELECT users.name, orders.product
FROM users
RIGHT JOIN orders ON users.id = orders.user_id;

RESULT:
┌───────────┬──────────┐
│ name      │ product  │
├───────────┼──────────┤
│ Rahul     │ Laptop   │
│ Rahul     │ Mouse    │
│ Priya     │ Keyboard │
│ NULL      │ Monitor  │  ← User not found
│ NULL      │ Headset  │  ← User not found
└───────────┴──────────┘

Note: सभी orders आए, भले ही user हो या न हो
```

#### 4. FULL OUTER JOIN (All records from both)

```sql
SELECT users.name, orders.product
FROM users
FULL OUTER JOIN orders ON users.id = orders.user_id;

RESULT:
┌───────────┬──────────┐
│ name      │ product  │
├───────────┼──────────┤
│ Rahul     │ Laptop   │
│ Rahul     │ Mouse    │
│ Priya     │ Keyboard │
│ Amit      │ NULL     │
│ Sneha     │ NULL     │
│ NULL      │ Monitor  │
│ NULL      │ Headset  │
└───────────┴──────────┘

Note: Everyone और everything आ गया
```

### JOIN Interview Questions

```sql
-- Q: Users जो orders नहीं किए
SELECT name FROM users
LEFT JOIN orders ON users.id = orders.user_id
WHERE orders.id IS NULL;
-- Result: Amit, Sneha

-- Q: Orders जिनका user नहीं मिला
SELECT orders.product FROM orders
LEFT JOIN users ON orders.user_id = users.id
WHERE users.id IS NULL;
-- Result: Monitor, Headset

-- Q: Total spending per user
SELECT users.name, SUM(orders.amount) as total_spent
FROM users
INNER JOIN orders ON users.id = orders.user_id
GROUP BY users.name;

-- Result:
-- Rahul: 50500
-- Priya: 2000
```

---

## <a name="data-validation"></a>Data Validation Testing

### Data Validation क्या है?

```
Data Validation = Data सही है या नहीं verify करना

TYPES OF VALIDATION:

1. FORMAT VALIDATION
   └─ Email format सही है?
   └─ Phone number format सही है?
   └─ Date format सही है?

2. RANGE VALIDATION
   └─ Age 0-150 के बीच है?
   └─ Price positive है?
   └─ Quantity negative तो नहीं?

3. REFERENTIAL INTEGRITY
   └─ Foreign key valid है?
   └─ Orphan records तो नहीं?

4. BUSINESS RULE VALIDATION
   └─ Discount 100% से तो नहीं?
   └─ Order total correct है?
```

### Data Validation Test Cases

```
SCENARIO: User Registration

TABLE: users
┌─────────────┬──────────────┬─────────────────┐
│ Column      │ Data Type    │ Constraints     │
├─────────────┼──────────────┼─────────────────┤
│ id          │ INT          │ PRIMARY KEY, AUTO_INCREMENT │
│ name        │ VARCHAR(100) │ NOT NULL        │
│ email       │ VARCHAR(255) │ NOT NULL, UNIQUE │
│ password    │ VARCHAR(255) │ NOT NULL        │
│ age         │ INT          │ CHECK (age >= 18) │
│ phone       │ VARCHAR(20)  │                 │
│ city        │ VARCHAR(50)  │ DEFAULT 'Delhi' │
│ created_at  │ DATETIME     │ DEFAULT NOW()   │
│ status      │ ENUM         │ ('active', 'inactive') │
└─────────────┴──────────────┴─────────────────┘
```

#### Validation Test Cases

```
┌────────────────────────────────────────────────────────────┐
│ POSITIVE TEST CASES                                       │
├────────────────────────────────────────────────────────────┤
│ TC001: Valid user registration → INSERT successful        │
│ TC002: User with all fields → All values saved correctly  │
│ TC003: User with minimum fields → Required fields saved   │
│ TC004: Default values → city='Delhi', status='active'     │
│ TC005: Auto-increment ID → Sequential IDs generate हुए    │
│ TC006: Timestamp → created_at current time आया            │
└────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────┐
│ NEGATIVE TEST CASES                                       │
├────────────────────────────────────────────────────────────┤
│ TC007: NULL name → Error (NOT NULL constraint)            │
│ TC008: NULL email → Error (NOT NULL constraint)           │
│ TC009: Duplicate email → Error (UNIQUE constraint)        │
│ TC010: Age < 18 → Error (CHECK constraint)                │
│ TC011: Age = 200 → Error or Warning (validation)          │
│ TC012: Invalid email format → Application level error     │
│ TC013: Name > 100 chars → Error (VARCHAR limit)           │
│ TC014: Special chars in name → Depends on validation      │
└────────────────────────────────────────────────────────────┘
```

### Data Validation SQL Queries

```sql
-- 1. Check for NULL values in required columns
SELECT * FROM users WHERE name IS NULL;
SELECT * FROM users WHERE email IS NULL;

-- 2. Check for duplicate emails
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;

-- 3. Check age range
SELECT * FROM users WHERE age < 18 OR age > 150;

-- 4. Check invalid email format
SELECT * FROM users 
WHERE email NOT LIKE '%@%.%';

-- 5. Check orphan records (orders without valid user)
SELECT * FROM orders
LEFT JOIN users ON orders.user_id = users.id
WHERE users.id IS NULL;

-- 6. Check data consistency
-- Total orders amount should match user's total spending
SELECT 
    u.name,
    SUM(o.amount) as total_spent
FROM users u
INNER JOIN orders o ON u.id = o.user_id
GROUP BY u.id, u.name
HAVING SUM(o.amount) < 0;  -- Negative spending? Bug!

-- 7. Check timestamp consistency
-- created_at should be before updated_at
SELECT * FROM users 
WHERE created_at > updated_at;

-- 8. Check enum values
SELECT * FROM users 
WHERE status NOT IN ('active', 'inactive');
```

---

## <a name="acid-properties"></a>ACID Properties Testing

### ACID Properties क्या हैं?

```
ACID = Database transactions की reliability guarantee करने के लिए

A - Atomicity
C - Consistency
I - Isolation
D - Durability
```

### 1. Atomicity (All or Nothing)

```
DEFINITION:
Transaction या तो completely complete होता है 
या completely fail होता है। Partial success नहीं होता।

EXAMPLE: Bank Transfer
┌─────────────────────────────────────────────────────────┐
│ Transfer ₹1000 from Account A to Account B             │
│                                                         │
│ Step 1: Deduct ₹1000 from A                            │
│ Step 2: Add ₹1000 to B                                 │
│                                                         │
│ Atomicity means:                                       │
│ ✓ Both steps succeed → Transaction complete           │
│ ✓ Either step fails → Both rollback (undo)            │
│                                                         │
│ NEVER:                                                  │
│ ✗ Step 1 success, Step 2 fail → Money lost!           │
└─────────────────────────────────────────────────────────┘

TEST CASES:
✓ Normal transfer → Both accounts update
✓ Insufficient funds → Both steps rollback
✓ Network failure mid-transaction → Rollback
✓ Database error → Rollback
```

### 2. Consistency (Rules Follow करना)

```
DEFINITION:
Transaction के before और after में database 
सभी defined rules follow करती है।

EXAMPLE: Account Balance
┌─────────────────────────────────────────────────────────┐
│ Business Rule: Balance कभी negative नहीं हो सकता       │
│                                                         │
│ Before Transaction:                                     │
│ Account A: ₹5000                                        │
│ Account B: ₹3000                                        │
│ Total: ₹8000                                            │
│                                                         │
│ After Transfer (₹1000 A → B):                          │
│ Account A: ₹4000                                        │
│ Account B: ₹4000                                        │
│ Total: ₹8000 ✓ (Consistent)                             │
│                                                         │
│ Invalid Scenario:                                       │
│ Account A: -₹1000  ✗ (Negative - Rule violated!)       │
└─────────────────────────────────────────────────────────┘

TEST CASES:
✓ Balance after transaction = Before - Transfer
✓ Balance never negative
✓ All constraints (FK, UNIQUE, CHECK) pass
✓ Triggers correctly execute हुए
```

### 3. Isolation (Independent Execution)

```
DEFINITION:
Multiple transactions एक साथ चल रही हों, तो 
एक दूसरे को affect नहीं करतीं।

EXAMPLE: Concurrent Transfers
┌─────────────────────────────────────────────────────────┐
│ Initial Balance: Account A = ₹10000                    │
│                                                         │
│ Transaction 1: A → B (₹3000)                           │
│ Transaction 2: A → C (₹4000)                           │
│                                                         │
│ WITHOUT Isolation (PROBLEM):                           │
│ T1 reads A: ₹10000                                     │
│ T2 reads A: ₹10000  ← T1 का change नहीं देखा!         │
│ T1 writes A: ₹7000                                     │
│ T2 writes A: ₹6000  ← Wrong! Should be ₹3000          │
│                                                         │
│ WITH Isolation (CORRECT):                              │
│ T1 completes fully → A = ₹7000                         │
│ T2 then executes → A = ₹3000 ✓                         │
└─────────────────────────────────────────────────────────┘

TEST CASES:
✓ Concurrent transactions don't interfere
✓ Final balance correct आता है
✓ No deadlocks (या properly handled)
✓ Locking mechanism works
```

### 4. Durability (Permanent Changes)

```
DEFINITION:
Transaction commit होने के बाद, changes permanent हैं।
System crash भी data lose नहीं कर सकता।

EXAMPLE: Payment Confirmation
┌─────────────────────────────────────────────────────────┐
│ User ने payment किया → "Payment Successful" दिखा       │
│                                                         │
│ Durability means:                                       │
│ ✓ Database में save हो गया                             │
│ ✓ Power failure हुआ → Data safe                       │
│ ✓ Server restart हुआ → Data still there               │
│ ✓ Hard disk fail हुआ → Backup से recover              │
│                                                         │
│ WITHOUT Durability (DISASTER):                         │
│ "Payment Successful" दिखा                              │
│ Server crash हुआ                                       │
│ Restart के बाद → Payment record नहीं मिला!             │
│ Customer angry!                                        │
└─────────────────────────────────────────────────────────┘

TEST CASES:
✓ Commit के बाद data persist होता है
✓ System restart के बाद data intact है
✓ Backup और recovery mechanisms work
✓ Transaction logs properly maintain होते हैं
```

### ACID Testing Checklist

```
ATOMICITY TESTING:
□ Multi-step transactions test करो
□ Mid-transaction failures simulate करो
□ Rollback properly हो रहा है verify करो
□ Partial updates नहीं हो रहे confirm करो

CONSISTENCY TESTING:
□ All constraints define करो
□ Before/after transaction data compare करो
□ Business rules enforce हो रहे हैं check करो
□ Triggers और stored procedures test करो

ISOLATION TESTING:
□ Concurrent transactions test करो
□ Race conditions identify करो
□ Locking mechanisms verify करो
□ Deadlock scenarios test करो

DURABILITY TESTING:
□ Commit के बाद data verify करो
□ System restart के बाद check करो
□ Backup recovery test करो
□ Transaction logs verify करो
```

---

## <a name="integrity-testing"></a>Database Integrity Testing

### Types of Integrity

```
┌────────────────────────────────────────────────────────────┐
│              DATABASE INTEGRITY TYPES                      │
├────────────────────────────────────────────────────────────┤
│ Type              │ Description         │ Example          │
├────────────────────────────────────────────────────────────┤
│ Entity Integrity  │ Primary Key unique │ No duplicate IDs  │
│ Domain Integrity  │ Valid data types   │ Age = number      │
│ Referential       │ Foreign Key valid  │ Order → Valid User│
│ Integrity         │                    │                   │
│ User-defined      │ Business rules     │ Balance >= 0      │
│ Integrity         │                    │                   │
└────────────────────────────────────────────────────────────┘
```

### Integrity Test Cases

```
SCENARIO: E-commerce Database

TABLES:
- users (id, name, email)
- products (id, name, price, stock)
- orders (id, user_id, product_id, quantity, total)
- order_items (id, order_id, product_id, quantity, price)
```

#### Entity Integrity Tests

```sql
-- Primary Key uniqueness
SELECT id, COUNT(*) 
FROM users 
GROUP BY id 
HAVING COUNT(*) > 1;
-- Result should be empty (no duplicates)

-- NOT NULL constraint
SELECT * FROM users WHERE id IS NULL;
-- Should return 0 rows

-- Auto-increment continuity
SELECT id FROM users ORDER BY id;
-- Check for unexpected gaps
```

#### Domain Integrity Tests

```sql
-- Data type validation
SELECT * FROM products WHERE price < 0;
-- Negative prices? Bug!

SELECT * FROM orders WHERE quantity <= 0;
-- Zero or negative quantity? Bug!

-- Enum/Check constraint
SELECT * FROM orders 
WHERE status NOT IN ('pending', 'processing', 'shipped', 'delivered', 'cancelled');
-- Invalid status? Bug!

-- Date validation
SELECT * FROM orders WHERE order_date > NOW();
-- Future orders? Data issue!

SELECT * FROM orders WHERE delivery_date < order_date;
-- Delivery before order? Impossible!
```

#### Referential Integrity Tests

```sql
-- Orphan orders (user doesn't exist)
SELECT o.* FROM orders o
LEFT JOIN users u ON o.user_id = u.id
WHERE u.id IS NULL;
-- Should be empty

-- Orphan order items (order doesn't exist)
SELECT oi.* FROM order_items oi
LEFT JOIN orders o ON oi.order_id = o.id
WHERE o.id IS NULL;
-- Should be empty

-- Invalid product references
SELECT oi.* FROM order_items oi
LEFT JOIN products p ON oi.product_id = p.id
WHERE p.id IS NULL;
-- Should be empty

-- Cascade delete test
-- Delete user → Orders should also delete (if CASCADE)
-- या Error देना चाहिए (if RESTRICT)
```

#### User-defined Integrity Tests

```sql
-- Business Rule: Order total = quantity × price
SELECT o.id, o.total, 
       SUM(oi.quantity * oi.price) as calculated_total
FROM orders o
JOIN order_items oi ON o.id = oi.order_id
GROUP BY o.id, o.total
HAVING o.total != SUM(oi.quantity * oi.price);
-- Mismatch? Calculation bug!

-- Business Rule: Stock can't be negative
SELECT * FROM products WHERE stock < 0;
-- Negative stock? Bug!

-- Business Rule: Discount can't exceed 100%
SELECT * FROM products WHERE discount_percentage > 100;
-- Invalid discount? Bug!

-- Business Rule: Email must be unique
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
-- Duplicate emails? Bug!
```

---

## <a name="query-optimization"></a>Query Optimization for Testers

### Why Testers Should Know Optimization?

```
REAL SCENARIOS:

1. SLOW REPORT
   Business: "Monthly report 10 minutes ले रहा है"
   Tester: Query analyze करके bottleneck find करेगा

2. TIMEOUT ERRORS
   User: "Page load नहीं हो रहा"
   Tester: Slow query identify करेगा

3. PERFORMANCE TESTING
   Load testing में database response time check करना

4. BUG INVESTIGATION
   "Query चल रही है पर data नहीं आ रहा"
   Tester: Query execution plan check करेगा
```

### Slow Query Identify करना

```sql
-- Enable slow query log (MySQL)
SET GLOBAL slow_query_log = 'ON';
SET GLOBAL long_query_time = 2;  -- 2 seconds से slow queries log

-- Check slow queries
SELECT * FROM mysql.slow_log;
```

### Query Optimization Tips

```
1. USE INDEXES
   Without Index: 1000 rows scan → Slow
   With Index: Direct row find → Fast
   
   CREATE INDEX idx_email ON users(email);
   SELECT * FROM users WHERE email = 'test@test.com';  -- Fast!

2. AVOID SELECT *
   Bad: SELECT * FROM users;  -- All columns fetch
   Good: SELECT id, name FROM users;  -- Only needed columns

3. USE WHERE EFFICIENTLY
   Bad: WHERE YEAR(created_at) = 2026  -- Function on column
   Good: WHERE created_at >= '2026-01-01' 
         AND created_at < '2027-01-01'  -- Index use होगा

4. AVOID N+1 QUERY PROBLEM
   Bad (N+1 queries):
   FOR each user:
       SELECT * FROM orders WHERE user_id = user.id
   
   Good (2 queries):
   SELECT * FROM users;
   SELECT * FROM orders WHERE user_id IN (1,2,3,...);

5. USE LIMIT FOR LARGE TABLES
   SELECT * FROM users LIMIT 100;  -- First 100 rows only

6. AVOID LIKE WITH LEADING WILDCARD
   Bad: WHERE name LIKE '%john%'  -- Index use नहीं होगा
   Good: WHERE name LIKE 'john%'  -- Index use होगा
```

### EXPLAIN Command

```sql
-- Query execution plan देखने के लिए
EXPLAIN SELECT * FROM users WHERE email = 'test@test.com';

RESULT COLUMNS:
┌──────────────────────────────────────────────────────────┐
│ id │ select_type │ table │ type  │ key     │ rows      │
├──────────────────────────────────────────────────────────┤
│ 1  │ SIMPLE      │ users │ ref   │ idx_email │ 1       │
└──────────────────────────────────────────────────────────┘

KEY COLUMNS TO CHECK:
- type: 'ALL' = Full table scan (BAD)
        'ref'/'range' = Index used (GOOD)
- key: NULL = No index used (BAD)
       index_name = Index used (GOOD)
- rows: कम = Fast, ज्यादा = Slow
```

### Performance Test Cases

```
┌────────────────────────────────────────────────────────────┐
│ PERFORMANCE TEST CASES                                    │
├────────────────────────────────────────────────────────────┤
│ TC001: Simple SELECT < 100ms                              │
│ TC002: JOIN query < 500ms                                 │
│ TC003: Aggregation query < 1s                             │
│ TC004: Bulk INSERT (1000 rows) < 5s                       │
│ TC005: Complex report query < 10s                         │
│ TC006: Concurrent queries (10 users) - all < 2s          │
│ TC007: Database under load - response time degradation   │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="real-scenarios"></a>Real Database Testing Scenarios

### Scenario 1: E-commerce Order Flow

```
DATABASE TABLES INVOLVED:
- users (customer)
- products (items)
- orders (order header)
- order_items (order products)
- payments (payment info)
- inventory (stock tracking)

FLOW:
1. User adds to cart → inventory में hold
2. User checks out → order create
3. Payment process → payment record
4. Order confirm → inventory update
5. Ship order → status update

TEST CASES:

┌───────────────────────────────────────────────────────────┐
│ DATA VALIDATION TEST CASES                                │
├───────────────────────────────────────────────────────────┤
│ 1. Order created → All tables में data consistent है    │
│ 2. Order total = SUM(order_items.total)                  │
│ 3. Payment amount = Order amount                          │
│ 4. Inventory reduced after order                          │
│ 5. Order status flow: pending → processing → shipped     │
│ 6. Cancelled order → inventory वापस बढ़ी                 │
│ 7. Refund → payment record update हुआ                    │
└───────────────────────────────────────────────────────────┘

SQL QUERIES FOR VALIDATION:

-- 1. Order total validation
SELECT o.id, o.total_amount, SUM(oi.subtotal) as calculated
FROM orders o
JOIN order_items oi ON o.id = oi.order_id
GROUP BY o.id
HAVING o.total_amount != SUM(oi.subtotal);

-- 2. Payment match validation
SELECT o.id, o.total_amount, p.amount
FROM orders o
JOIN payments p ON o.id = p.order_id
WHERE o.total_amount != p.amount;

-- 3. Inventory check
SELECT p.id, p.name, p.stock, 
       SUM(oi.quantity) as ordered_qty
FROM products p
LEFT JOIN order_items oi ON p.id = oi.product_id
LEFT JOIN orders o ON oi.order_id = o.id AND o.status != 'cancelled'
GROUP BY p.id
HAVING p.stock < 0;  -- Negative stock? Bug!
```

### Scenario 2: Banking Application

```
CRITICAL TABLES:
- accounts (account info)
- transactions (all transactions)
- users (customer info)

KEY REQUIREMENTS:
✓ Balance कभी negative नहीं (unless overdraft)
✓ हर transaction का record रहे
✓ Debit = Credit (double entry)
✓ Audit trail maintain रहे

TEST CASES:

┌───────────────────────────────────────────────────────────┐
│ BANKING DATA TEST CASES                                   │
├───────────────────────────────────────────────────────────┤
│ 1. Account balance = Opening + Credits - Debits          │
│ 2. No negative balance (without overdraft)               │
│ 3. Transaction timestamps sequential हैं                 │
│ 4. Duplicate transaction नहीं है                         │
│ 5. Interest calculation correct है                       │
│ 6. Tax deducted at source (TDS) recorded है             │
│ 7. Audit log में हर action recorded है                  │
└───────────────────────────────────────────────────────────┘

CRITICAL SQL QUERIES:

-- Balance verification
SELECT a.account_number, a.current_balance,
       (a.opening_balance + 
        SUM(CASE WHEN t.type = 'credit' THEN t.amount ELSE 0 END) -
        SUM(CASE WHEN t.type = 'debit' THEN t.amount ELSE 0 END)
       ) as calculated_balance
FROM accounts a
JOIN transactions t ON a.id = t.account_id
GROUP BY a.id
HAVING a.current_balance != calculated_balance;

-- Negative balance check
SELECT * FROM accounts WHERE current_balance < 0 
AND overdraft_limit = 0;  -- No overdraft allowed

-- Duplicate transaction check
SELECT transaction_ref, COUNT(*) 
FROM transactions 
GROUP BY transaction_ref 
HAVING COUNT(*) > 1;

-- Timestamp anomaly (future transactions)
SELECT * FROM transactions WHERE transaction_date > NOW();
```

### Scenario 3: Data Migration Testing

```
SCENARIO: Old System → New System migration

MIGRATION TYPES:
1. Database to Database
2. Excel/CSV to Database
3. Legacy System to Modern System

TESTING APPROACH:

┌───────────────────────────────────────────────────────────┐
│ MIGRATION TESTING CHECKLIST                               │
├───────────────────────────────────────────────────────────┤
│ PRE-MIGRATION:                                            │
│ □ Source data count note किया                            │
│ □ Data quality check किया                                │
│ □ Backup ले लिया                                        │
│ □ Migration script test की                               │
├───────────────────────────────────────────────────────────┤
│ DURING MIGRATION:                                         │
│ □ Error logs monitor किए                                 │
│ □ Failed records tracked किए                            │
│ □ Rollback plan ready रखा                               │
├───────────────────────────────────────────────────────────┤
│ POST-MIGRATION:                                           │
│ □ Record count match हुआ                               │
│ □ Sample data verify किया                                │
│ □ Aggregations match हुए                                │
│ □ Relationships intact हैं                              │
│ □ Application testing की                                │
└───────────────────────────────────────────────────────────┘

VALIDATION QUERIES:

-- Record count comparison
SELECT 'Old' as source, COUNT(*) as count FROM old_db.users
UNION
SELECT 'New' as source, COUNT(*) as count FROM new_db.users;
-- Counts should match

-- Sample data comparison
SELECT o.id, o.name, o.email, n.name, n.email
FROM old_db.users o
JOIN new_db.users n ON o.id = n.id
WHERE o.name != n.name OR o.email != n.email;
-- Should return 0 rows

-- Aggregation comparison
SELECT 
    (SELECT COUNT(*) FROM old_db.orders) as old_orders,
    (SELECT COUNT(*) FROM new_db.orders) as new_orders,
    (SELECT SUM(total) FROM old_db.orders) as old_total,
    (SELECT SUM(total) FROM new_db.orders) as new_total;
-- All should match
```

---

## <a name="database-tools"></a>Database Testing Tools

### Popular Database Tools

```
┌────────────────────────────────────────────────────────────┐
│                  DATABASE TOOLS                            │
├────────────────────────────────────────────────────────────┤
│ Tool              │ Database    │ Platform  │ Cost        │
├────────────────────────────────────────────────────────────┤
│ MySQL Workbench   │ MySQL       │ All       │ Free        │
│ pgAdmin           │ PostgreSQL  │ All       │ Free        │
│ SQL Server Mgmt   │ SQL Server  │ Windows   │ Free        │
│ Oracle SQL Dev    │ Oracle      │ All       │ Free        │
│ DBeaver           │ Multiple    │ All       │ Free        │
│ HeidiSQL          │ MySQL, PG   │ Windows   │ Free        │
│ Navicat           │ Multiple    │ All       │ Paid        │
│ DataGrip          │ Multiple    │ All       │ Paid        │
└────────────────────────────────────────────────────────────┘
```

### DBeaver Tutorial (Recommended for Testers)

```
WHY DBeaver?
✓ Multiple database support (MySQL, PG, Oracle, etc.)
✓ Free Community Edition
✓ User-friendly interface
✓ Query execution और export
✓ Data comparison features
✓ ER diagrams

DOWNLOAD: https://dbeaver.io/download

BASIC USAGE:

1. CONNECTION SETUP
   └─ Database Connect click करो
   └─ Database type select करो (MySQL, PostgreSQL, etc.)
   └─ Host, Port, Database name डालो
   └─ Username, Password डालो
   └─ Test Connection click करो
   └─ Finish!

2. BROWSE DATA
   └─ Database navigator में tables देखो
   └─ Table पे double-click करो
   └─ Data grid में data देखो

3. EXECUTE QUERIES
   └─ SQL Editor open करो
   └─ Query लिखो
   └─ Ctrl+Enter या Execute button click करो
   └─ Results नीचे देखो

4. EXPORT DATA
   └─ Results पे right-click करो
   └─ Export Data select करो
   └─ Format choose करो (CSV, Excel, etc.)
   └─ File path select करो
   └─ Finish!

5. COMPARE DATA
   └─ Tools → Compare/Move
   └─ Source और target select करो
   └─ Differences देखो
```

### SQL Query Templates for Testers

```sql
-- Template 1: Data Count Summary
SELECT 
    'users' as table_name, COUNT(*) as count FROM users
UNION ALL
SELECT 'orders', COUNT(*) FROM orders
UNION ALL
SELECT 'products', COUNT(*) FROM products;

-- Template 2: Recent Records
SELECT * FROM orders 
ORDER BY created_at DESC 
LIMIT 10;

-- Template 3: Find Duplicates
SELECT email, COUNT(*) as duplicate_count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;

-- Template 4: Data Quality Check
SELECT 
    'NULL emails' as issue, COUNT(*) as count 
    FROM users WHERE email IS NULL
UNION ALL
SELECT 'Invalid phones', COUNT(*) 
    FROM users WHERE phone NOT LIKE '%_______%'
UNION ALL
SELECT 'Negative balances', COUNT(*) 
    FROM accounts WHERE balance < 0;

-- Template 5: Orphan Records
SELECT o.* FROM orders o
LEFT JOIN users u ON o.user_id = u.id
WHERE u.id IS NULL;

-- Template 6: Data Consistency Check
SELECT 
    SUM(CASE WHEN condition1 THEN 1 ELSE 0 END) as issue1_count,
    SUM(CASE WHEN condition2 THEN 1 ELSE 0 END) as issue2_count
FROM your_table;
```

---

## <a name="best-practices"></a>Best Practices & Common Issues

### Database Testing Best Practices

```
1. ALWAYS USE TEST ENVIRONMENT
   ✗ Production में direct queries मत चलाओ
   ✓ Test/Staging environment use करो

2. BACKUP BEFORE TESTING
   ✓ Important queries से पहले backup लो
   ✓ Rollback plan रखो

3. USE TRANSACTIONS FOR TESTING
   BEGIN;  -- Start transaction
   -- Your test queries
   ROLLBACK;  -- Undo everything
   -- या
   COMMIT;  -- Save changes

4. DOCUMENT YOUR QUERIES
   ✓ Test queries save करो
   ✓ Comments add करो
   ✓ Team के साथ share करो

5. VALIDATE AT MULTIPLE LEVELS
   ✓ UI से data enter करो
   ✓ Database में verify करो
   ✓ API से data enter करो
   ✓ Database में verify करो

6. CHECK DATA INTEGRITY REGULARLY
   ✓ Weekly data quality checks
   ✓ Monthly integrity audits

7. MONITOR SLOW QUERIES
   ✓ Performance baseline set करो
   ✓ Degradation track करो
```

### Common Database Issues

```
┌────────────────────────────────────────────────────────────┐
│              COMMON DATABASE ISSUES                        │
├────────────────────────────────────────────────────────────┤
│ Issue              │ Symptoms           │ Detection        │
├────────────────────────────────────────────────────────────┤
│ Duplicate Records  │ Data inconsistency │ GROUP BY + HAVING│
├────────────────────────────────────────────────────────────┤
│ Orphan Records     │ Broken relations   │ LEFT JOIN + NULL │
├────────────────────────────────────────────────────────────┤
│ NULL in Required   │ Application errors │ IS NULL check    │
│ Fields             │                    │                  │
├────────────────────────────────────────────────────────────┤
│ Data Type Mismatch │ Insert failures    │ Type validation  │
├────────────────────────────────────────────────────────────┤
│ Constraint         │ Unexpected errors  │ Constraint check │
│ Violations         │                    │                  │
├────────────────────────────────────────────────────────────┤
│ Slow Queries       │ Timeout errors     │ EXPLAIN, logs    │
├────────────────────────────────────────────────────────────┤
│ Deadlocks          │ Application hang   │ Error logs       │
├────────────────────────────────────────────────────────────┤
│ Data Corruption    │ Wrong calculations │ Aggregation check│
└────────────────────────────────────────────────────────────┘
```

### Database Testing Checklist

```
┌────────────────────────────────────────────────────────────┐
│           DATABASE TESTING CHECKLIST                       │
├────────────────────────────────────────────────────────────┤
│ STRUCTURE TESTING:                                         │
□ Tables created correctly                                   │
□ Columns have correct data types                            │
□ Constraints defined (PK, FK, UNIQUE, NOT NULL, CHECK)     │
□ Indexes created for performance                            │
□ Triggers and stored procedures compile                     │
├────────────────────────────────────────────────────────────┤
│ DATA TESTING:                                              │
□ Data insert working                                        │
□ Data update working                                        │
□ Data delete working                                        │
□ NULL handling correct                                      │
□ Default values working                                     │
□ Auto-increment working                                     │
├────────────────────────────────────────────────────────────┤
│ INTEGRITY TESTING:                                         │
□ Primary Key unique है                                      │
□ Foreign Key valid हैं                                     │
□ No orphan records                                          │
□ Referential actions work (CASCADE, RESTRICT)              │
□ Business rules enforced                                    │
├────────────────────────────────────────────────────────────┤
│ PERFORMANCE TESTING:                                       │
□ Queries response time acceptable                           │
□ Indexes being used (EXPLAIN check)                         │
□ No table scans on large tables                             │
□ Concurrent access handled                                  │
□ Locking doesn't cause deadlocks                            │
├────────────────────────────────────────────────────────────┤
│ SECURITY TESTING:                                          │
□ User permissions correct                                   │
□ Sensitive data encrypted                                   │
□ SQL injection prevented                                    │
□ Audit logging enabled                                      │
└────────────────────────────────────────────────────────────┘
```

---

## <a name="interview-questions"></a>20+ Interview Questions

### Fundamentals (1-5)

**Q1. Database testing क्यों जरूरी है?**
```
A: Database testing जरूरी है क्योंकि:
- Data integrity maintain रहती है
- Data accuracy verify होती है
- Business rules enforce होती हैं
- Performance issues early मिलते हैं
- Security vulnerabilities पकड़ में आते हैं
- UI testing से backend bugs नहीं मिलते
```

**Q2. SQL में DDL, DML, DQL क्या है?**
```
A:
DDL (Data Definition Language): Database structure
- CREATE, ALTER, DROP, TRUNCATE

DML (Data Manipulation Language): Data operations
- INSERT, UPDATE, DELETE

DQL (Data Query Language): Data retrieval
- SELECT
```

**Q3. Primary Key और Foreign Key में difference?**
```
A:
Primary Key:
- Table का unique identifier
- NULL नहीं हो सकता
- एक table में एक ही PK

Foreign Key:
- दूसरी table का Primary Key reference करता है
- NULL हो सकता है
- Relationship establish करता है
```

**Q4. INNER JOIN और LEFT JOIN में difference?**
```
A:
INNER JOIN: सिर्फ matching records दोनों tables से
LEFT JOIN: सभी records left table से + matching right table से

Example:
Users (1,2,3,4) और Orders (user 1,2,5 के)
INNER JOIN: user 1,2 के orders
LEFT JOIN: user 1,2 के orders + 3,4 के NULL
```

**Q5. ACID properties क्या हैं?**
```
A:
Atomicity: All or nothing
Consistency: Rules follow करना
Isolation: Independent execution
Durability: Permanent changes
```

### SQL Queries (6-12)

**Q6. Duplicate records कैसे find करोगे?**
```sql
A: 
SELECT email, COUNT(*) as count
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

**Q7. Second highest salary कैसे find करोगे?**
```sql
A:
-- Method 1: LIMIT
SELECT DISTINCT salary FROM employees
ORDER BY salary DESC
LIMIT 1 OFFSET 1;

-- Method 2: Subquery
SELECT MAX(salary) FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Q8. Orphan records कैसे find करोगे?**
```sql
A:
SELECT o.* FROM orders o
LEFT JOIN users u ON o.user_id = u.id
WHERE u.id IS NULL;
```

**Q9. NULL values कैसे check करते हैं?**
```sql
A:
-- NULL check
SELECT * FROM users WHERE email IS NULL;

-- NOT NULL check
SELECT * FROM users WHERE email IS NOT NULL;

Note: = NULL काम नहीं करता, IS NULL use करो
```

**Q10. LIKE operator कैसे use करते हैं?**
```sql
A:
-- Starts with 'A'
WHERE name LIKE 'A%'

-- Ends with 'h'
WHERE name LIKE '%h'

-- Contains 'oh'
WHERE name LIKE '%oh%'

-- Single character
WHERE name LIKE 'R_hul'  -- Rahul, Rohit
```

**Q11. GROUP BY और HAVING में difference?**
```
A:
GROUP BY: Rows को group करता है
HAVING: Groups को filter करता है

Example:
SELECT city, COUNT(*) as user_count
FROM users
GROUP BY city
HAVING COUNT(*) > 100;
-- Cities with more than 100 users
```

**Q12. UNION और UNION ALL में difference?**
```
A:
UNION: Duplicate rows remove करता है
UNION ALL: Duplicate rows keep करता है (faster)

UNION थोड़ा slow है क्योंकि duplicates remove करने के लिए sort करता है
```

### Scenario-Based (13-18)

**Q13. Data migration testing कैसे करते हैं?**
```
A:
1. Pre-migration: Source data count और quality check
2. During migration: Error logs monitor
3. Post-migration:
   - Record count match
   - Sample data comparison
   - Aggregation match (SUM, COUNT)
   - Relationships intact हैं check
   - Application testing
```

**Q14. Database performance issue कैसे debug करते हो?**
```
A:
1. Slow query logs check करता हूं
2. EXPLAIN से execution plan देखता हूं
3. Index usage verify करता हूं
4. Table scan तो नहीं हो रहा check करता हूं
5. Query optimization suggest करता हूं
6. Database configuration check करता हूं
```

**Q15. Transaction rollback कैसे test करते हैं?**
```
A:
BEGIN;  -- Transaction start
-- Multiple operations
-- Force error somewhere
ROLLBACK;  -- Should undo everything

Verify:
- कोई partial update नहीं हुआ
- सभी tables में data unchanged है
```

**Q16. Concurrent transactions के issues कैसे test करते हो?**
```
A:
- Multiple sessions से same data update
- Race conditions simulate
- Deadlock scenarios test
- Final data consistency check
- Lock timeouts verify
```

**Q17. Database में data corruption कैसे identify करोगे?**
```
A:
- Aggregation mismatches (totals don't match)
- Orphan records suddenly appear
- Constraint violations
- Unexpected NULL values
- Calculation errors in reports
- Application errors with valid data
```

**Q18. Index क्या है और कब use करना चाहिए?**
```
A:
Index = Book की index जैसा, fast lookup के लिए

USE INDEX WHEN:
✓ WHERE clause में column use हो
✓ JOIN columns पर
✓ ORDER BY columns पर
✓ Large tables में

DON'T USE WHEN:
✗ Small tables (< 1000 rows)
✗ Frequently updated columns
✗ Low cardinality columns (Gender, Status)
```

### Advanced (19-22)

**Q19. View क्या है और कब use करते हैं?**
```
A:
View = Virtual table (query result)

USE CASES:
✓ Complex queries simplify करने के लिए
✓ Security (sensitive columns hide)
✓ Consistent logic across application
✓ Backward compatibility

CREATE VIEW active_users AS
SELECT id, name, email FROM users WHERE status = 'active';
```

**Q20. Stored Procedure और Function में difference?**
```
A:
Stored Procedure:
- Multiple statements
- IN/OUT parameters
- Return multiple values
- CALL करके execute

Function:
- Single expression
- IN parameters only
- Return single value
- SELECT में use कर सकते
```

**Q21. Trigger क्या है? Testing कैसे करते हैं?**
```
A:
Trigger = Automatic action on INSERT/UPDATE/DELETE

Example: Order insert hone पर inventory update

TESTING:
✓ Trigger fire हो रहा है
✓ Correct logic execute हो रहा
✓ Performance impact नहीं है
✓ Recursive triggers नहीं हैं
```

**Q22. Database normalization क्या है?**
```
A:
Normalization = Redundancy कम करना

1NF: Atomic values (no comma-separated)
2NF: 1NF + no partial dependency
3NF: 2NF + no transitive dependency

Benefits:
✓ Less redundancy
✓ Better integrity
✓ Easier maintenance

Trade-off:
✗ More JOINs needed
✗ Can be slower
```

---

## 🎯 Quick Reference: SQL Cheat Sheet

```
BASIC QUERIES:
SELECT * FROM table;              -- All data
SELECT col1, col2 FROM table;     -- Specific columns
SELECT * FROM table WHERE id=1;   -- With filter
SELECT * FROM table LIMIT 10;     -- First 10 rows

JOINS:
INNER JOIN  → Matching only
LEFT JOIN   → All from left + matching
RIGHT JOIN  → All from right + matching
FULL JOIN   → Everything

AGGREGATIONS:
COUNT(*)    → Row count
SUM(col)    → Total
AVG(col)    → Average
MIN(col)    → Minimum
MAX(col)    → Maximum

CONSTRAINTS:
PRIMARY KEY → Unique identifier
FOREIGN KEY → Reference to other table
NOT NULL    → Required field
UNIQUE      → No duplicates
CHECK       → Value validation
DEFAULT     → Default value
```

---

*Module 08 Complete ✅*  
*Next: Module 09 - Web Application Testing (Already exists, will be reviewed)*
