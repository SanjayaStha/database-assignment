# **Module 5: Practical Database Implementation**

## **5.1 Using DBMS Tools**

### **Overview of Tools: MySQL, PostgreSQL, MS SQL Server**

- **MySQL**: An open-source relational database management system (RDBMS) widely used for web applications. MySQL is known for its speed, reliability, and ease of use. It supports a wide range of operating systems and is commonly paired with PHP and Apache in the LAMP stack (Linux, Apache, MySQL, PHP).

- **PostgreSQL**: An advanced open-source RDBMS that emphasizes extensibility and standards compliance. PostgreSQL supports advanced data types (e.g., JSON, XML) and is known for its strong ACID compliance, making it a reliable choice for complex, large-scale applications.

- **MS SQL Server**: A relational database management system developed by Microsoft. It is designed for high-performance applications and integrates well with other Microsoft products. MS SQL Server supports a wide range of features, including stored procedures, triggers, and business intelligence tools.

### **Installing and Setting Up a DBMS**

- **MySQL**: To install MySQL, follow the steps below:
  1. Download the MySQL installer from the official website.
  2. Follow the installation wizard to install MySQL on your machine.
  3. Start the MySQL service.
  4. Use the MySQL Workbench or command-line interface to create and manage databases.

  Example of creating a database in MySQL:
CREATE DATABASE TestDB;




- **PostgreSQL**: To install PostgreSQL, follow these steps:
1. Download the PostgreSQL installer from the official website.
2. Run the installer and follow the on-screen instructions.
3. Once installed, launch pgAdmin, the PostgreSQL management tool.
4. Create a new database and connect to it.

Example of creating a database in PostgreSQL:
CREATE DATABASE TestDB;

sql


- **MS SQL Server**: To install MS SQL Server, follow these steps:
1. Download the MS SQL Server installer from the official Microsoft website.
2. Install the SQL Server software and SQL Server Management Studio (SSMS).
3. After installation, open SSMS to connect to the server and manage databases.

Example of creating a database in MS SQL Server:
CREATE DATABASE TestDB;

sql


## **5.2 ERD to Database Implementation**

### **Creating Tables from ERDs**

An Entity-Relationship Diagram (ERD) is a graphical representation of the database structure, which shows entities (tables) and relationships between them. To implement a database from an ERD, follow these steps:

1. **Identify Entities**: Each entity in the ERD corresponds to a table in the database.
2. **Define Attributes**: The attributes of each entity become the columns of the table.
3. **Define Primary Keys**: Identify the unique identifiers for each entity (usually represented by a key in the ERD). This becomes the primary key of the table.
4. **Define Foreign Keys**: Identify relationships between entities. Foreign keys in a table are used to reference the primary key of another table.

#### **Example**

If you have an ERD with two entities, `Customer` and `Order`, the ERD might look like this:

- **Customer**: CustomerID (PK), FirstName, LastName, Email
- **Order**: OrderID (PK), CustomerID (FK), OrderDate, TotalAmount

In SQL, you would create these tables as follows:
CREATE TABLE Customer ( CustomerID INT PRIMARY KEY, FirstName VARCHAR(50), LastName VARCHAR(50), Email VARCHAR(100) );

CREATE TABLE Order ( OrderID INT PRIMARY KEY, CustomerID INT, OrderDate DATE, TotalAmount DECIMAL(10, 2), FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID) );


### **Defining Relationships and Constraints**

Relationships between tables are defined using **foreign keys** and **constraints**.

- **One-to-Many Relationship**: One record in the parent table is associated with multiple records in the child table. This is implemented using a foreign key.
  Example: A customer can have multiple orders, so `CustomerID` in the `Order` table would be a foreign key referencing `Customer(CustomerID)`.

- **Many-to-Many Relationship**: This type of relationship requires a third table (junction table) to store the associations. For example, a student can enroll in multiple courses, and a course can have multiple students. The junction table stores the combination of `StudentID` and `CourseID`.

  Example:
CREATE TABLE Student ( StudentID INT PRIMARY KEY, Name VARCHAR(50) );

CREATE TABLE Course ( CourseID INT PRIMARY KEY, CourseName VARCHAR(100) );

CREATE TABLE Enrollment ( StudentID INT, CourseID INT, PRIMARY KEY (StudentID, CourseID), FOREIGN KEY (StudentID) REFERENCES Student(StudentID), FOREIGN KEY (CourseID) REFERENCES Course(CourseID) );




## **5.3 Database Maintenance**

### **Backups and Recovery**

Database backup and recovery are crucial for protecting data and ensuring it can be restored in case of failures. There are different types of backups:

1. **Full Backup**: A complete copy of the entire database, including all tables and data.
2. **Incremental Backup**: Only the changes made since the last backup are copied.
3. **Differential Backup**: Copies all changes made since the last full backup.

To perform backups, you can use tools provided by your DBMS, such as MySQL’s `mysqldump`, PostgreSQL’s `pg_dump`, or MS SQL Server’s `BACKUP` command.

#### **Example of Backup in MySQL**
```sql 
mysqldump -u username -p TestDB > backup.sql
```

#### **Example of Backup in PostgreSQL**
```
pg_dump TestDB > backup.sql
```
#### **Example of Backup in MS SQL Server**
```sql
BACKUP DATABASE TestDB TO DISK = 'C:\Backup\TestDB.bak';
```


### **User Management and Permissions**

User management and permissions control who can access and modify the database. Database administrators (DBAs) create users and assign them specific roles or privileges.

- **Creating Users**: You can create a new user with the following SQL command.

  MySQL:
```
CREATE USER 'username'@'localhost' IDENTIFIED BY 'password';
```
makefile


PostgreSQL:
```
CREATE USER username WITH PASSWORD 'password';
```
MS SQL Server:
```
CREATE LOGIN username WITH PASSWORD = 'password';
```



- **Granting Permissions**: After creating a user, you assign them permissions to access or modify database objects.

MySQL:
```
GRANT ALL PRIVILEGES ON TestDB.* TO 'username'@'localhost';
```

PostgreSQL:
```
GRANT ALL PRIVILEGES ON DATABASE TestDB TO username;
```
MS SQL Server:
```
GRANT SELECT, INSERT, UPDATE, DELETE ON TestDB TO username;
```



- **Revoking Permissions**: To revoke access or privileges, use the REVOKE command.

MySQL:
```
REVOKE ALL PRIVILEGES ON TestDB.* FROM 'username'@'localhost';
```

PostgreSQL:
```
REVOKE ALL PRIVILEGES ON DATABASE TestDB FROM username;
```
MS SQL Server:
```
REVOKE SELECT, INSERT, UPDATE, DELETE ON TestDB TO username;
```
sql


Database maintenance tasks like backups, user management, and performance monitoring are essential for keeping the database secure, efficient, and recoverable in case of failure.












