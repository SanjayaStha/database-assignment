
---

## **Module 1: Introduction to the `ALTER` Statement**
**Definition:**  
The `ALTER` statement is used to modify existing database structures like tables, columns, constraints, and indexes.  

**Example (Checking Table Structure Before and After Alteration):**  
```sql
-- Check table structure (MS SQL & MySQL)
DESC Customers;
```

---

## **Module 2: Altering Tables – Adding and Removing Columns**  
### **Adding a Column**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers ADD Age INT;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers ADD COLUMN Age INT AFTER LastName;
```

### **Removing a Column**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers DROP COLUMN Age;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers DROP COLUMN Age;
```

---

## **Module 3: Modifying Column Data Types and Constraints**  
### **Changing Column Data Type**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers ALTER COLUMN Age BIGINT;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers MODIFY Age BIGINT;
```

### **Adding and Removing `NOT NULL` Constraints**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers ALTER COLUMN Age INT NOT NULL;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers MODIFY Age INT NOT NULL;
```

---

## **Module 4: Renaming Columns and Tables**  
### **Renaming a Column**  
#### **MS SQL Server:**  
```sql
EXEC sp_rename 'Customers.Age', 'CustomerAge', 'COLUMN';
```
#### **MySQL:**  
```sql
ALTER TABLE Customers RENAME COLUMN Age TO CustomerAge;
```

### **Renaming a Table**  
#### **MS SQL Server:**  
```sql
EXEC sp_rename 'Customers', 'ClientList';
```
#### **MySQL:**  
```sql
ALTER TABLE Customers RENAME TO ClientList;
```

---

## **Module 5: Adding and Removing Constraints**  
### **Adding a Primary Key**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers ADD CONSTRAINT PK_Customer PRIMARY KEY (CustomerID);
```
#### **MySQL:**  
```sql
ALTER TABLE Customers ADD PRIMARY KEY (CustomerID);
```

### **Removing a Primary Key**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Customers DROP CONSTRAINT PK_Customer;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers DROP PRIMARY KEY;
```

### **Adding a Foreign Key**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Orders ADD CONSTRAINT FK_Customer FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID);
```
#### **MySQL:**  
```sql
ALTER TABLE Orders ADD CONSTRAINT FK_Customer FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID);
```

### **Removing a Foreign Key**  
#### **MS SQL Server:**  
```sql
ALTER TABLE Orders DROP CONSTRAINT FK_Customer;
```
#### **MySQL:**  
```sql
ALTER TABLE Orders DROP FOREIGN KEY FK_Customer;
```

---

<!-- ## **Module 6: Working with Indexes**  
### **Adding an Index**  
#### **MS SQL Server:**  
```sql
CREATE INDEX idx_lastname ON Customers(LastName);
```
#### **MySQL:**  
```sql
ALTER TABLE Customers ADD INDEX idx_lastname (LastName);
```

### **Removing an Index**  
#### **MS SQL Server:**  
```sql
DROP INDEX idx_lastname ON Customers;
```
#### **MySQL:**  
```sql
ALTER TABLE Customers DROP INDEX idx_lastname;
```

---

<!-- ## **Module 7: Altering Views and Stored Procedures**  
### **Modifying a View**  
#### **MS SQL Server:**  
```sql
ALTER VIEW CustomerView AS 
SELECT CustomerID, FirstName, LastName FROM Customers;
```
#### **MySQL:**  
```sql
CREATE OR REPLACE VIEW CustomerView AS 
SELECT CustomerID, FirstName, LastName FROM Customers;
```

### **Modifying a Stored Procedure**  
#### **MS SQL Server:**  
```sql
ALTER PROCEDURE GetCustomers AS 
SELECT * FROM Customers WHERE Age > 18;
```
#### **MySQL:**  
```sql
DELIMITER //
CREATE PROCEDURE GetCustomers()
BEGIN
    SELECT * FROM Customers WHERE Age > 18;
END //
DELIMITER ;
```

---

## **Module 8: Performance Considerations and Best Practices**  
- **Always take backups before altering a table.**  
- **For large tables, use transactions to prevent locking.**  
- **Avoid dropping columns frequently, as it may lead to fragmentation.**  
- **Check index performance before adding or dropping indexes.**  

--- --> -->


---
<!-- 
### **Exercise 2: Optimize Index Usage in an E-commerce Database**
1. Add an index to the `Orders` table on `OrderDate`.  
2. Remove an unused index from the `Customers` table.  

#### **Solution:**  
```sql
ALTER TABLE Orders ADD INDEX idx_orderdate (OrderDate);
ALTER TABLE Customers DROP INDEX idx_unused;
```

Here’s a **comprehensive practice set** with **30 SQL ALTER statement exercises**, covering various scenarios for **MS SQL Server and MySQL**.  

--- -->

## **📝 Sample Table: `Employees`**
To start, create a sample table to practice `ALTER` operations:  

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Age INT,
    DepartmentID INT,
    HireDate DATE
);
```
## ** Hands-on Exercises and Case Studies**  
### **Exercise 1: Modify the Schema of an Employee Database**
1. Add a column `Salary` to the `Employees` table.  
2. Rename the column `Salary` to `MonthlySalary`.  
3. Change the data type of `MonthlySalary` to `DECIMAL(10,2)`.  
4. Add a `NOT NULL` constraint to `MonthlySalary`.  
5. Add a foreign key from `Employees` to a `Departments` table.  

#### **Solution (MS SQL Server & MySQL):**  
```sql
ALTER TABLE Employees ADD Salary DECIMAL(10,2);
ALTER TABLE Employees RENAME COLUMN Salary TO MonthlySalary;
ALTER TABLE Employees MODIFY MonthlySalary DECIMAL(10,2) NOT NULL;
ALTER TABLE Employees ADD CONSTRAINT FK_Dept FOREIGN KEY (DeptID) REFERENCES Departments(DeptID);
```

---

# **🛠️ Practice Questions on ALTER TABLE**
## **📌 Section 1: Adding and Removing Columns (5 Questions)**  
### **Q1:** Add a new column `Salary` (DECIMAL(10,2)) to the `Employees` table.  
```sql
ALTER TABLE Employees ADD Salary DECIMAL(10,2);
```

### **Q2:** Remove the `Age` column from the `Employees` table.  
```sql
ALTER TABLE Employees DROP COLUMN Age;
```

### **Q3:** Add a column `Email` (VARCHAR(100)) after `LastName` (only in MySQL).  
```sql
ALTER TABLE Employees ADD COLUMN Email VARCHAR(100) AFTER LastName;
```

### **Q4:** Add a `PhoneNumber` column (VARCHAR(15)) and make it unique.  
```sql
ALTER TABLE Employees ADD PhoneNumber VARCHAR(15) UNIQUE;
```

### **Q5:** Remove the `PhoneNumber` column from the `Employees` table.  
```sql
ALTER TABLE Employees DROP COLUMN PhoneNumber;
```

---

## **📌 Section 2: Modifying Column Data Types and Constraints (5 Questions)**  
### **Q6:** Change the data type of `Salary` to `FLOAT`.  
```sql
ALTER TABLE Employees ALTER COLUMN Salary FLOAT;
```
(For MySQL: `ALTER TABLE Employees MODIFY Salary FLOAT;`)

### **Q7:** Make `LastName` column **NOT NULL**.  
```sql
ALTER TABLE Employees ALTER COLUMN LastName VARCHAR(50) NOT NULL;
```
(For MySQL: `ALTER TABLE Employees MODIFY LastName VARCHAR(50) NOT NULL;`)

### **Q8:** Change `HireDate` to `DATETIME` instead of `DATE`.  
```sql
ALTER TABLE Employees ALTER COLUMN HireDate DATETIME;
```

### **Q9:** Increase the `FirstName` column size from 50 to 100.  
```sql
ALTER TABLE Employees ALTER COLUMN FirstName VARCHAR(100);
```

### **Q10:** Set a default value of `10000` for `Salary`.  
```sql
ALTER TABLE Employees ADD CONSTRAINT DF_Salary DEFAULT 10000 FOR Salary;
```
(MySQL: `ALTER TABLE Employees ALTER Salary SET DEFAULT 10000;`)

---

## **📌 Section 3: Renaming Columns and Tables (5 Questions)**  
### **Q11:** Rename the column `FirstName` to `EmpFirstName`.  
```sql
EXEC sp_rename 'Employees.FirstName', 'EmpFirstName', 'COLUMN';
```
(MySQL: `ALTER TABLE Employees RENAME COLUMN FirstName TO EmpFirstName;`)

### **Q12:** Rename the table `Employees` to `Staff`.  
```sql
EXEC sp_rename 'Employees', 'Staff';
```
(MySQL: `ALTER TABLE Employees RENAME TO Staff;`)

### **Q13:** Rename the column `HireDate` to `JoiningDate`.  
```sql
ALTER TABLE Employees RENAME COLUMN HireDate TO JoiningDate;
```

### **Q14:** Rename the column `LastName` to `Surname`.  
```sql
EXEC sp_rename 'Employees.LastName', 'Surname', 'COLUMN';
```

### **Q15:** Rename `Salary` to `MonthlySalary`.  
```sql
ALTER TABLE Employees RENAME COLUMN Salary TO MonthlySalary;
```

---

## **📌 Section 4: Adding and Removing Constraints (5 Questions)**  
### **Q16:** Add a `PRIMARY KEY` to the `EmployeeID` column.  
```sql
ALTER TABLE Employees ADD CONSTRAINT PK_Employee PRIMARY KEY (EmployeeID);
```

### **Q17:** Remove the `PRIMARY KEY` from `EmployeeID`.  
```sql
ALTER TABLE Employees DROP CONSTRAINT PK_Employee;
```

### **Q18:** Add a `FOREIGN KEY` constraint on `DepartmentID` referencing `Departments(DepartmentID)`.  
```sql
ALTER TABLE Employees ADD CONSTRAINT FK_Department FOREIGN KEY (DepartmentID) REFERENCES Departments(DepartmentID);
```

### **Q19:** Remove the `FOREIGN KEY` constraint on `DepartmentID`.  
```sql
ALTER TABLE Employees DROP CONSTRAINT FK_Department;
```

### **Q20:** Add a `CHECK` constraint to ensure `Salary` is greater than 5000.  
```sql
ALTER TABLE Employees ADD CONSTRAINT CHK_Salary CHECK (Salary > 5000);
```

---
<!-- 
## **📌 Section 5: Working with Indexes (5 Questions)**  
### **Q21:** Add an index on the `LastName` column.  
```sql
CREATE INDEX idx_lastname ON Employees(LastName);
```
(MySQL: `ALTER TABLE Employees ADD INDEX idx_lastname (LastName);`)

### **Q22:** Remove the index on `LastName`.  
```sql
DROP INDEX idx_lastname ON Employees;
```
(MySQL: `ALTER TABLE Employees DROP INDEX idx_lastname;`)

### **Q23:** Add a unique index on the `Email` column.  
```sql
CREATE UNIQUE INDEX idx_email ON Employees(Email);
```

### **Q24:** Add a composite index on `LastName` and `FirstName`.  
```sql
CREATE INDEX idx_name ON Employees(LastName, FirstName);
```

### **Q25:** Remove the composite index on `LastName` and `FirstName`.  
```sql
DROP INDEX idx_name ON Employees;
``` -->

---
<!-- 
## **📌 Section 6: Altering Views and Stored Procedures (5 Questions)**  
### **Q26:** Create a view `EmpView` that selects `EmployeeID`, `FirstName`, and `Salary`.  
```sql
CREATE VIEW EmpView AS 
SELECT EmployeeID, FirstName, Salary FROM Employees;
```

### **Q27:** Alter `EmpView` to include `DepartmentID`.  
```sql
ALTER VIEW EmpView AS 
SELECT EmployeeID, FirstName, Salary, DepartmentID FROM Employees;
```

### **Q28:** Drop the `EmpView` view.  
```sql
DROP VIEW EmpView;
```

### **Q29:** Create a stored procedure `GetHighSalaryEmployees` that selects employees with salary > 10000.  
```sql
CREATE PROCEDURE GetHighSalaryEmployees
AS
SELECT * FROM Employees WHERE Salary > 10000;
```

### **Q30:** Alter the stored procedure `GetHighSalaryEmployees` to filter for salary > 15000.  
```sql
ALTER PROCEDURE GetHighSalaryEmployees
AS
SELECT * FROM Employees WHERE Salary > 15000;
``` -->
