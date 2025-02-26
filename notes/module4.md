# Module 4: Structured Query Language (SQL)

## 4.1 Basics of SQL

### Data Definition Language (DDL)

**Data Definition Language (DDL)** commands are used to define and modify the structure of a database, including tables, views, and schemas.

- **CREATE:** Used to create database objects like tables, views, or indexes. 
```sql
CREATE TABLE Students ( StudentID INT PRIMARY KEY, FirstName VARCHAR(50), LastName VARCHAR(50), Age INT );
```

- **ALTER:** Used to modify an existing database object. 
```sql
ALTER TABLE Students ADD Email VARCHAR(100);
```

- **DROP:** Used to delete an existing database object. 
```sql
DROP TABLE Students;
```

### Data Manipulation Language (DML)

**Data Manipulation Language (DML)** commands are used for data retrieval and manipulation.

- **INSERT:** Adds new records to a table. 
```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age) VALUES (1, 'John', 'Doe', 22);
```

- **SELECT:** Retrieves data from one or more tables. 
```sql 
SELECT FirstName, LastName FROM Students WHERE Age > 18;
```

- **UPDATE**: Modifies existing data in a table. 
```sql
UPDATE Students SET Age = 23 WHERE StudentID = 1;
```

- **DELETE**: Removes records from a table. 
```sql
DELETE FROM Students WHERE StudentID = 1;
```

## 4.2 SQL Constraints

- **NOT NULL** Ensures that a column cannot have a NULL value. 
```sql 
CREATE TABLE Employees ( EmployeeID INT NOT NULL, Name VARCHAR(100) NOT NULL, Age INT );
```

- **UNIQUE** Ensures that all values in a column are unique. 
```sql
CREATE TABLE Employees ( EmployeeID INT, Email VARCHAR(100) UNIQUE );
```

- **CHECK** Ensures that values in a column satisfy a specific condition. 
```sql 
CREATE TABLE Employees ( EmployeeID INT, Age INT CHECK (Age >= 18) );
```

- **DEFAULT** Specifies a default value for a column when no value is provided. 
```sql
CREATE TABLE Employees ( EmployeeID INT, Department VARCHAR(50) DEFAULT 'HR' );
```

- **FOREIGN KEY** Enforces a link between two tables. 
```sql
CREATE TABLE Orders ( OrderID INT, EmployeeID INT, FOREIGN KEY (EmployeeID) REFERENCES Employees(EmployeeID) );
```

- **AUTO_INCREMENT** constraint is used to automatically generate a unique value for a column, typically for a primary key. This constraint ensures that each new row inserted into the table gets a unique value for the column, usually incremented by 1 from the last value inserted.
```sql 
CREATE TABLE table_name (
    column_name INT AUTO_INCREMENT,
    other_column datatype,
    PRIMARY KEY (column_name)
);

```

## 4.3 Advanced SQL

### Joins

**INNER JOIN:** Returns records that have matching values in both tables. 
```sql 
SELECT Employees.Name, Orders.OrderID FROM Employees INNER JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
```

**LEFT JOIN:** Returns all records from the left table and matching records from the right table. 
```sql 
SELECT Employees.Name, Orders.OrderID FROM Employees LEFT JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
```

**RIGHT JOIN:** Returns all records from the right table and matching records from the left table. 
``` sql 
SELECT Employees.Name, Orders.OrderID FROM Employees RIGHT JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
```

**FULL JOIN:** Returns all records when there is a match in either left or right table. 
```sql 
SELECT Employees.Name, Orders.OrderID FROM Employees FULL JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
```

![alt text](image-1.png)

**Subqueries and Nested Queries** A subquery is a query within another query, often used in the WHERE or FROM clause.

```SQL 
SELECT Name FROM Employees WHERE EmployeeID IN (SELECT EmployeeID FROM Orders WHERE OrderAmount > 1000);
```

### Aggregation Functions

Aggregation functions are used to perform a calculation on a set of values and return a single value.

**COUNT:** Counts the number of rows. ```SELECT COUNT(*) FROM Orders;```

**SUM:** Adds up values in a numeric column. ```SELECT SUM(OrderAmount) FROM Orders;```

**AVG:** Calculates the average of a numeric column. ```SELECT AVG(Age) FROM Employees;```

**MAX:** Returns the maximum value in a column. ```SELECT MAX(Age) FROM Employees;```

**MIN:** Returns the minimum value in a column. ```SELECT MIN(Age) FROM Employees;```

### SQL OPERATORS

### 1. **`LIKE`**
   - **Purpose**: Used to search for a specified pattern in a column.
   - **Wildcards**:
     - `%` (represents zero or more characters)
     - `_` (represents a single character)
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Name LIKE 'A%';
     SELECT * FROM Employees WHERE Name LIKE 'J___';

     ```
     **Use case**: 
        - Finding all employees whose names start with 'A'.
        - Finding all employess whose names start with 'J' and has exactly 4 letters.
        - J: The first character is fixed as 'J'.
        - ___: The three underscores represent exactly three more characters (making a total of 4 characters).

### 2. **`BETWEEN`**
   - **Purpose**: Selects values within a range (inclusive of the boundary values).
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Salary BETWEEN 40000 AND 70000;
     ```
     **Use case**: Finding employees with salaries between 40,000 and 70,000.

### 3. **`AND`**
   - **Purpose**: Combines multiple conditions; all conditions must be true.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Age > 30 AND Department = 'HR';
     ```
     **Use case**: Finding employees older than 30 who are in the HR department.

### 4. **`OR`**
   - **Purpose**: Combines multiple conditions; any condition can be true.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Department = 'HR' OR Department = 'Sales';
     ```
     **Use case**: Finding employees who are in either the HR or Sales department.

### 5. **`NOT`**
   - **Purpose**: Negates a condition.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE NOT Department = 'HR';
     ```
     **Use case**: Finding employees who are not in the HR department.

### 6. **`IN`**
   - **Purpose**: Checks if a value matches any value within a list.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Department IN ('Sales', 'HR', 'IT');
     ```
     **Use case**: Finding employees in any of the listed departments.

### 7. **`IS NULL`**
   - **Purpose**: Checks if a column contains a `NULL` value.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE ManagerID IS NULL;
     ```
     **Use case**: Finding employees without a manager assigned.

### 8. **`IS NOT NULL`**
   - **Purpose**: Checks if a column does not contain a `NULL` value.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE ManagerID IS NOT NULL;
     ```
     **Use case**: Finding employees who have a manager assigned.

### 9. **`EXISTS`**
   - **Purpose**: Checks if a subquery returns any results.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE EXISTS (SELECT * FROM Departments WHERE Employees.DepartmentID = Departments.DepartmentID);
     ```
     **Use case**: Finding employees who belong to an existing department.

### 10. **`ANY`**
   - **Purpose**: Compares a value to each value in a list or subquery and returns true if the condition is true for any value in the list.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Salary > ANY (SELECT Salary FROM Employees WHERE Department = 'Sales');
     ```
     **Use case**: Finding employees whose salary is greater than at least one employee in the Sales department.

### 11. **`ALL`**
   - **Purpose**: Compares a value to each value in a list or subquery and returns true if the condition is true for all values in the list.
   - **Example**:
     ```sql
     SELECT * FROM Employees WHERE Salary > ALL (SELECT Salary FROM Employees WHERE Department = 'HR');
     ```
     **Use case**: Finding employees whose salary is greater than all employees in the HR department.

### 12. **`ORDER BY`**
   - **Purpose**: Sorts the result set in ascending (ASC) or descending (DESC) order.
   - **Example**:
     ```sql
     SELECT * FROM Employees ORDER BY Salary DESC;
     ```
     **Use case**: Sorting employees by salary in descending order.

### 13. **`DISTINCT`**
   - **Purpose**: Removes duplicate values from the result set.
   - **Example**:
     ```sql
     SELECT DISTINCT Department FROM Employees;
     ```
     **Use case**: Finding unique departments.

### 14. **`GROUP BY`**
   - **Purpose**: Groups rows that have the same values into summary rows.
   - **Example**:
     ```sql
     SELECT Department, COUNT(*) FROM Employees GROUP BY Department;
     ```
     **Use case**: Counting the number of employees in each department.

### 15. **`HAVING`**
   - **Purpose**: Filters records after a `GROUP BY` operation, similar to `WHERE` but for aggregated data.
   - **Example**:
     ```sql
     SELECT Department, COUNT(*) FROM Employees GROUP BY Department HAVING COUNT(*) > 5;
     ```
     **Use case**: Finding departments with more than 5 employees.

### 16. **`JOIN`** (INNER, LEFT, RIGHT, FULL)
   - **Purpose**: Combines rows from two or more tables based on a related column.
     - **INNER JOIN**: Returns matching records from both tables.
     - **LEFT JOIN**: Returns all records from the left table and matching records from the right table.
     - **RIGHT JOIN**: Returns all records from the right table and matching records from the left table.
     - **FULL JOIN**: Returns all records when there is a match in either the left or right table.
   - **Example** (INNER JOIN):
     ```sql
     SELECT Employees.Name, Departments.Name
     FROM Employees
     INNER JOIN Departments ON Employees.DepartmentID = Departments.DepartmentID;
     ```
     **Use case**: Joining employees with their respective departments.

### 17. **`NULLIF`**
   - **Purpose**: Returns `NULL` if two expressions are equal.
   - **Example**:
     ```sql
     SELECT NULLIF(Salary, 10000) FROM Employees;
     ```
     **Use case**: Avoiding division by zero by returning `NULL` if the salary is 10000.

### 18. **`COALESCE`**
   - **Purpose**: Returns the first non-NULL value in the list of expressions.
   - **Example**:
     ```sql
     SELECT COALESCE(PhoneNumber, 'N/A') FROM Employees;
     ```
     **Use case**: Displaying 'N/A' if the phone number is `NULL`.

### 19. **`LIMIT`**
   - **Purpose**: Restricts the number of records returned by a query.
   - **Example**:
     ```sql
     SELECT * FROM Employees LIMIT 5;
     ```
     **Use case**: Limiting the result set to the first 5 rows.

### 20. **`OFFSET`**
   - **Purpose**: Skips a number of rows before starting to return rows.
   - **Example**:
     ```sql
     SELECT * FROM Employees LIMIT 5 OFFSET 5;
     ```
     **Use case**: Skipping the first 5 rows and returning the next 5 rows.

### 21. **`CASE`**
   - **Purpose**: Performs conditional logic in queries.
   - **Example**:
     ```sql
     SELECT Name, CASE 
                    WHEN Salary > 50000 THEN 'High'
                    ELSE 'Low'
                  END AS SalaryCategory
     FROM Employees;
     ```
     **Use case**: Categorizing employees into 'High' or 'Low' salary categories.

These operators, when used correctly, allow for complex querying, filtering, grouping, and conditional logic in SQL. They are fundamental to efficiently working with SQL databases and performing sophisticated operations.
## 4.4 Database Transactions

### ACID Properties

The ACID properties guarantee that database transactions are processed reliably:

- **Atomicity**: The transaction is treated as a single unit, which either completes entirely or not at all.
- **Consistency**: The database is always in a valid state before and after the transaction.
- **Isolation**: Transactions are isolated from each other until they are completed.
- **Durability**: Once a transaction is committed, it will remain in the database, even if there is a system failure.

### Transaction Control Commands

- **COMMIT**: Saves the changes made in a transaction. COMMIT;

- **ROLLBACK**: Undoes changes made in the current transaction. ROLLBACK;

- **SAVEPOINT**: Sets a point within a transaction to which you can roll back. SAVEPOINT SavePoint1;

## 4.5 Indexing and Optimization

### Purpose of Indexing

- Indexes are used to improve the speed of data retrieval operations on a database table. They can speed up SELECT queries but may slow down INSERT, UPDATE, and DELETE operations.


- Creating an Index 
```sql
CREATE INDEX idx_lastname ON Employees (LastName);
```

### Query Optimization Basics

- Limit the use of ```SELECT *```: Always specify the columns you need. SELECT Name, Age FROM Employees;

- Use JOIN instead of subqueries when possible: Joins are generally more efficient. 
```sql
SELECT Employees.Name, Orders.OrderID FROM Employees JOIN Orders ON Employees.EmployeeID = Orders.EmployeeID;
```

- Index frequently used columns: Indexes speed up queries that filter or sort by these columns.

### Example of Optimized Query

- An unoptimized query: 
```sql
SELECT * FROM Orders WHERE OrderAmount > 1000 AND OrderDate > '2024-01-01';
```

- An optimized query with an index on OrderAmount and OrderDate: 
```sql 
CREATE INDEX idx_orderamount_date ON Orders (OrderAmount, OrderDate);
```

```sql
SELECT OrderID, OrderAmount FROM Orders WHERE OrderAmount > 1000 AND OrderDate > '2024-01-01';
```