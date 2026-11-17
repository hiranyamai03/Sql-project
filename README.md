# Library Management System – MySQL

## 1. Project Description

The Library Management System is a database project developed using MySQL to manage library operations efficiently. It stores information about books, authors, members, borrowing transactions, and fines.

This project focuses on database design, data management, and retrieving meaningful information using SQL queries. It demonstrates intermediate-level MySQL concepts through multiple tables and their relationships.

## 2. Features

- Store and manage author details.
- Maintain book information, prices, and availability.
- Manage library member records.
- Track book borrowing and returning transactions.
- Maintain fine details and payment status.
- Generate reports using SQL queries.
- Retrieve information using joins and subqueries.
- Create views for frequently used reports.
- Use stored procedures for reusable SQL operations.

## 3. Technologies Used

- **Database:** MySQL
- **Language:** SQL
- **Tool:** MySQL Workbench

## 4. Database Structure

The project contains five tables:

| Table Name | Description |
|---|---|
| Authors | Stores author details such as name and country. |
| Books | Stores book details, author ID, category, price, and availability. |
| Members | Stores library member information and contact details. |
| Borrowings | Tracks book borrowing, due dates, and return status. |
| Fines | Stores fine amounts and payment status. |

## 5. Table Relationships

- Authors and Books – One-to-Many relationship.
- Books and Borrowings – One-to-Many relationship.
- Members and Borrowings – One-to-Many relationship.
- Borrowings and Fines – One-to-One relationship in the sample dataset.

Foreign keys are used to maintain relationships between the tables.

## 6. SQL Concepts Covered

### Database Operations
- CREATE DATABASE
- CREATE TABLE
- INSERT INTO
- UPDATE
- DELETE
- ALTER TABLE

### SQL Queries
- SELECT
- WHERE
- ORDER BY
- GROUP BY
- HAVING
- DISTINCT
- LIMIT

### Joins
- INNER JOIN
- LEFT JOIN
- RIGHT JOIN
- CROSS JOIN
- Multiple-table joins

### Subqueries
- Single-row subqueries
- Multiple-row subqueries
- Nested subqueries
- Correlated subqueries
- EXISTS and NOT EXISTS
- ANY and ALL operators

### SQL Functions
- Aggregate functions: COUNT(), SUM(), AVG(), MIN(), MAX()
- String functions: CONCAT(), UPPER(), LOWER(), LENGTH()
- Numeric functions: ROUND(), ABS(), MOD()
- Date functions: DATEDIFF(), DATE_ADD(), YEAR(), MONTH()
- Conditional functions: IF(), IFNULL(), COALESCE()
- CASE expressions

### Advanced SQL Concepts
- Window functions
- Views
- Stored procedures
- IN, OUT, and INOUT parameters

## 7. Views

Views are created to simplify complex queries and generate reusable reports.

Some views included in the project:

- Book and author details.
- Member borrowing history.
- Member borrowing count.
- Book availability report.
- Member fine details.
- Category-wise average book price.
- Author-wise book count.
- Borrowing statistics.
- Fine payment summary.
- Overdue books report.
- Monthly borrowing report.
- Complete library report.

## 8. Stored Procedures

Stored procedures are created to execute reusable SQL operations.

Some procedures included:

- GetAllBooks()
- GetAllMembers()
- GetBooksByCategory()
- GetMemberBorrowingHistory()
- GetCurrentlyBorrowedBooks()
- GetOverdueBooks()
- GetUnpaidFines()
- CountBooksByCategory()
- GetMemberTotalFine()
- GetAuthorBookCount()
- GetFrequentMembers()
- UpdateBookPrice()
- UpdateFineStatus()
- GetLibraryReport()

## 9. Installation Steps

1. Install MySQL Server and MySQL Workbench.
2. Open MySQL Workbench.
3. Connect to your MySQL server.
4. Create a new SQL script.
5. Execute the database and table creation queries.
6. Insert the sample records into all five tables.
7. Execute the SQL queries, views, and stored procedures.

## 10. How to Execute SQL Files

Execute the SQL scripts in the following order:

1. `01_create_database_tables.sql` – Creates the database and five tables.
2. `02_insert_records.sql` – Inserts sample records into the tables.
3. `03_basic_queries.sql` – Contains basic SQL queries and functions.
4. `04_joins_subqueries.sql` – Contains joins, subqueries, and correlated subqueries.
5. `05_window_functions.sql` – Contains window function queries.
6. `06_views.sql` – Creates views for reporting.
7. `07_stored_procedures.sql` – Creates reusable stored procedures.

Open each SQL file in MySQL Workbench and execute it in the given order.

## 11. Sample Queries

### 1. Display all books with author names

```sql
SELECT b.book_title, a.author_name, b.category, b.price
FROM Books b
INNER JOIN Authors a
ON b.author_id = a.author_id;
```

### 2. Find members who borrowed more than one book

```sql
SELECT m.member_name, COUNT(br.borrowing_id) AS total_borrowings
FROM Members m
INNER JOIN Borrowings br
ON m.member_id = br.member_id
GROUP BY m.member_id, m.member_name
HAVING COUNT(br.borrowing_id) > 1;
```

### 3. Find books priced above the average book price

```sql
SELECT book_title, price
FROM Books
WHERE price > (SELECT AVG(price) FROM Books);
```

### 4. Display unpaid fines

```sql
SELECT fine_id, borrowing_id, fine_amount, payment_status
FROM Fines
WHERE payment_status = 'Unpaid';
```

### 5. Display the most expensive book

```sql
SELECT book_title, price
FROM Books
WHERE price = (SELECT MAX(price) FROM Books);
```

## 12. Future Enhancements

- Add a book reservation system.
- Implement automatic fine calculation.
- Add a book search feature.
- Generate monthly and yearly library reports.
- Add user authentication and role-based access.
- Develop a web-based interface for library management.

## 13. Project Outcome

This project provides practical experience in relational database design and SQL query development. It demonstrates the ability to manage structured data, establish table relationships, retrieve information using complex queries, and generate reports using views and stored procedures.
