Here’s a **practice set** of SQL questions related to a **Banking System**, focusing on CRUD operations and constraints. These questions can help you practice SQL queries for a banking domain.

### **1. Create Table Queries**
#### Question 1:
Create a table `Customers` with the following columns:
- `CustomerID` (Primary Key, Auto Increment)
- `FirstName` (VARCHAR(50))
- `LastName` (VARCHAR(50))
- `Email` (VARCHAR(100), Unique)
- `PhoneNumber` (VARCHAR(15))
- `Address` (VARCHAR(200))

#### Question 2:
Create a table `Accounts` with the following columns:
- `AccountNumber` (Primary Key)
- `CustomerID` (Foreign Key references `Customers.CustomerID`)
- `AccountType` (VARCHAR(20)) – values could be 'Saving', 'Checking', etc.
- `Balance` (Decimal)
- `DateCreated` (DATE)

### **2. Inserting Data**
#### Question 3:
Insert the following data into the `Customers` table:

| CustomerID | FirstName | LastName | Email                  | PhoneNumber | Address                |
|------------|-----------|----------|------------------------|-------------|------------------------|
| 1          | John      | Doe      | john.doe@email.com      | 1234567890  | 123 Main St, Cityville |
| 2          | Jane      | Smith    | jane.smith@email.com    | 0987654321  | 456 Elm St, Townville  |
| 3          | Mike      | Johnson  | mike.johnson@email.com  | 1122334455  | 789 Oak St, Villageville|

#### Question 4:
Insert the following data into the `Accounts` table:

| AccountNumber | CustomerID | AccountType | Balance | DateCreated |
|---------------|------------|-------------|---------|-------------|
| 1001          | 1          | Saving      | 5000.00 | 2023-01-15  |
| 1002          | 1          | Checking    | 1500.00 | 2023-02-20  |
| 1003          | 2          | Saving      | 2000.00 | 2023-03-01  |
| 1004          | 3          | Checking    | 3000.00 | 2023-03-10  |

### **3. Update Data**
#### Question 5:
Update the balance of the account with `AccountNumber` 1001 to 5500.00.

#### Question 6:
Update the `Email` of the customer with `CustomerID` 2 to `jane.smith@newdomain.com`.

#### Question 7:
Increase the balance by 10% for all customers with a `Saving` account type.

### **4. Select Queries**
#### Question 8:
Write a query to list the `CustomerID`, `FirstName`, `LastName`, and `Balance` of all customers who have a `Saving` account type.

#### Question 9:
Find all customers who have a balance greater than 3000.00 and their `AccountType` is `Checking`.

#### Question 10:
List all accounts with a balance less than 2000.00, along with the `CustomerID`, `AccountNumber`, and `AccountType`.

### **5. Deleting Data**
#### Question 11:
Delete the account with `AccountNumber` 1002.

#### Question 12:
Delete all customers whose `PhoneNumber` starts with "123".

#### Question 13:
Delete all accounts that have been created before `2023-02-01`.

### **6. Join Queries**
#### Question 14:
Write a query to find the `FirstName`, `LastName`, and `AccountType` of customers who have a balance greater than 2000.00.

#### Question 15:
Write a query to get the total balance of all `Saving` accounts, and show the `AccountType` and `TotalBalance`.

#### Question 16:
Write a query to show the customer’s `FirstName`, `LastName`, `AccountNumber`, and `Balance` from the `Customers` and `Accounts` tables. Ensure that it shows all customers, including those without an account.

### **7. Constraints and Validation**
#### Question 17:
Modify the `Accounts` table to ensure that the `Balance` column must never be negative.

#### Question 18:
Modify the `Customers` table to ensure that the `Email` column must be unique and not null.

#### Question 19:
Add a foreign key constraint to the `Accounts` table for the `CustomerID` column, linking it to the `CustomerID` column of the `Customers` table.

#### Question 20:
Create a check constraint on the `AccountType` column in the `Accounts` table to ensure that only 'Saving' or 'Checking' values are allowed.

### **8. Complex Queries**
#### Question 21:
Write a query to show the customer with the highest balance across all account types.

#### Question 22:
Write a query to transfer 1000.00 from the account with `AccountNumber` 1003 to the account with `AccountNumber` 1001. Ensure that both balances are updated correctly, and check that the accounts exist.

#### Question 23:
Create a report that shows the total balance for each customer, including their `FirstName` and `LastName`. If a customer has multiple accounts, the total should be the sum of all their account balances.

### **9. Aggregation**
#### Question 24:
Find the average balance of all accounts in the `BankingSystem`.

#### Question 25:
Write a query to count the total number of `Saving` accounts in the system.

### **10. Transactions**
#### Question 26:
Write a transaction that:
1. Withdraws 500.00 from the account with `AccountNumber` 1002.
2. Deposits 500.00 into the account with `AccountNumber` 1003.
3. Commits the transaction if both operations are successful.

---

Here are SQL queries for all the questions related to the banking system practice set:

---

### **1. Create Table Queries**

#### Question 1: Create `Customers` Table

```sql
CREATE TABLE Customers (
    CustomerID INT AUTO_INCREMENT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50),
    Email VARCHAR(100) UNIQUE,
    PhoneNumber VARCHAR(15),
    Address VARCHAR(200)
);
```

#### Question 2: Create `Accounts` Table

```sql
CREATE TABLE Accounts (
    AccountNumber INT PRIMARY KEY,
    CustomerID INT,
    AccountType VARCHAR(20),
    Balance DECIMAL(10, 2),
    DateCreated DATE,
    FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID)
);
```

---

### **2. Inserting Data**

#### Question 3: Insert Data into `Customers` Table

```sql
INSERT INTO Customers (FirstName, LastName, Email, PhoneNumber, Address)
VALUES 
('John', 'Doe', 'john.doe@email.com', '1234567890', '123 Main St, Cityville'),
('Jane', 'Smith', 'jane.smith@email.com', '0987654321', '456 Elm St, Townville'),
('Mike', 'Johnson', 'mike.johnson@email.com', '1122334455', '789 Oak St, Villageville');
```

#### Question 4: Insert Data into `Accounts` Table

```sql
INSERT INTO Accounts (AccountNumber, CustomerID, AccountType, Balance, DateCreated)
VALUES
(1001, 1, 'Saving', 5000.00, '2023-01-15'),
(1002, 1, 'Checking', 1500.00, '2023-02-20'),
(1003, 2, 'Saving', 2000.00, '2023-03-01'),
(1004, 3, 'Checking', 3000.00, '2023-03-10');
```

---

### **3. Update Data**

#### Question 5: Update Balance of Account 1001

```sql
UPDATE Accounts
SET Balance = 5500.00
WHERE AccountNumber = 1001;
```

#### Question 6: Update Email of Customer 2

```sql
UPDATE Customers
SET Email = 'jane.smith@newdomain.com'
WHERE CustomerID = 2;
```

#### Question 7: Increase Balance by 10% for All Saving Accounts

```sql
UPDATE Accounts
SET Balance = Balance * 1.10
WHERE AccountType = 'Saving';
```

---

### **4. Select Queries**

#### Question 8: List `CustomerID`, `FirstName`, `LastName`, `Balance` for Saving Account Holders

```sql
SELECT Customers.CustomerID, Customers.FirstName, Customers.LastName, Accounts.Balance
FROM Customers
JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID
WHERE Accounts.AccountType = 'Saving';
```

#### Question 9: Find Customers with Balance Greater Than 3000 and Account Type Checking

```sql
SELECT Customers.CustomerID, Customers.FirstName, Customers.LastName, Accounts.Balance
FROM Customers
JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID
WHERE Accounts.Balance > 3000 AND Accounts.AccountType = 'Checking';
```

#### Question 10: List All Accounts with Balance Less Than 2000

```sql
SELECT CustomerID, AccountNumber, AccountType, Balance
FROM Accounts
WHERE Balance < 2000;
```

---

### **5. Deleting Data**

#### Question 11: Delete Account with Account Number 1002

```sql
DELETE FROM Accounts
WHERE AccountNumber = 1002;
```

#### Question 12: Delete Customers Whose Phone Number Starts with '123'

```sql
DELETE FROM Customers
WHERE PhoneNumber LIKE '123%';
```

#### Question 13: Delete Accounts Created Before '2023-02-01'

```sql
DELETE FROM Accounts
WHERE DateCreated < '2023-02-01';
```

---

### **6. Join Queries**

#### Question 14: Find `FirstName`, `LastName`, and `AccountType` of Customers with Balance Greater Than 2000

```sql
SELECT Customers.FirstName, Customers.LastName, Accounts.AccountType
FROM Customers
JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID
WHERE Accounts.Balance > 2000;
```

#### Question 15: Get Total Balance of Saving Accounts

```sql
SELECT AccountType, SUM(Balance) AS TotalBalance
FROM Accounts
WHERE AccountType = 'Saving'
GROUP BY AccountType;
```

#### Question 16: Show Customer’s `FirstName`, `LastName`, `AccountNumber`, and `Balance`, Including Customers without Accounts

```sql
SELECT Customers.FirstName, Customers.LastName, Accounts.AccountNumber, Accounts.Balance
FROM Customers
LEFT JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID;
```

---

### **7. Constraints and Validation**

#### Question 17: Ensure `Balance` Cannot Be Negative

```sql
ALTER TABLE Accounts
ADD CONSTRAINT check_balance CHECK (Balance >= 0);
```

#### Question 18: Ensure `Email` Is Unique and Not Null

```sql
ALTER TABLE Customers
MODIFY COLUMN Email VARCHAR(100) NOT NULL UNIQUE;
```

#### Question 19: Add Foreign Key Constraint to `Accounts`

```sql
ALTER TABLE Accounts
ADD CONSTRAINT fk_customer FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID);
```

#### Question 20: Create Check Constraint for AccountType

```sql
ALTER TABLE Accounts
ADD CONSTRAINT check_account_type CHECK (AccountType IN ('Saving', 'Checking'));
```

---

### **8. Complex Queries**

#### Question 21: Find the Customer with the Highest Balance Across All Account Types

```sql
SELECT Customers.FirstName, Customers.LastName, Accounts.AccountNumber, MAX(Accounts.Balance) AS HighestBalance
FROM Customers
JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID
GROUP BY Customers.CustomerID
ORDER BY HighestBalance DESC
LIMIT 1;
```

#### Question 22: Transfer 1000 from Account 1003 to Account 1001

```sql
BEGIN TRANSACTION;

UPDATE Accounts
SET Balance = Balance - 1000
WHERE AccountNumber = 1003;

UPDATE Accounts
SET Balance = Balance + 1000
WHERE AccountNumber = 1001;

COMMIT;
```

#### Question 23: Show Total Balance for Each Customer

```sql
SELECT Customers.FirstName, Customers.LastName, SUM(Accounts.Balance) AS TotalBalance
FROM Customers
JOIN Accounts ON Customers.CustomerID = Accounts.CustomerID
GROUP BY Customers.CustomerID;
```

---

### **9. Aggregation**

#### Question 24: Find the Average Balance of All Accounts

```sql
SELECT AVG(Balance) AS AverageBalance
FROM Accounts;
```

#### Question 25: Count Total Number of Saving Accounts

```sql
SELECT COUNT(*) AS TotalSavingAccounts
FROM Accounts
WHERE AccountType = 'Saving';
```

---

### **10. Transactions**

#### Question 26: Withdraw from One Account and Deposit into Another

```sql
BEGIN TRANSACTION;

UPDATE Accounts
SET Balance = Balance - 500
WHERE AccountNumber = 1002;

UPDATE Accounts
SET Balance = Balance + 500
WHERE AccountNumber = 1003;

COMMIT;
```

---
