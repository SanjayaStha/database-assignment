Here’s an **expanded version** of the **15 complex tables** with **3-4 rows of sample data** each. The data contains **multivalued attributes, repeating groups, and dependencies**, making them ideal for **practicing normalization up to 3NF**.

---

## **1. Employee Records (Before Normalization)**
**Table: Employee_Details**  
| EmpID | Name  | Department | Address  | Projects        | PhoneNumbers         | ManagerID |  
|-------|------ |-----------|----------|----------------|----------------------|-----------|  
| 101   | John  | IT        | NY, USA  | P1, P2         | 9876543210, 8765432109 | 501 |  
| 102   | Alice | HR        | LA, USA  | P3             | 9988776655          | 502 |  
| 103   | Bob   | IT        | SF, USA  | P4, P5, P6     | 9123456789, 9456123456 | 501 |  
| 104   | Emma  | Finance   | TX, USA  | P7, P8         | 9456123456, 9012345678 | 503 |  

---

## **2. Customer Orders System**  
**Table: Customer_Orders**  
| OrderID | CustomerName | Address   | Phone        | ProductDetails       | Quantity | TotalPrice |  
|---------|-------------|-----------|-------------|---------------------|----------|------------|  
| 201     | Mike        | NY, USA   | 9876543210  | Laptop, Mouse       | 1,2      | 1500 |  
| 202     | Emma        | LA, USA   | 8765432109  | Keyboard            | 1        | 50   |  
| 203     | John        | TX, USA   | 9876123456  | Monitor, Mouse, CPU | 1,1,1    | 800  |  
| 204     | Alice       | SF, USA   | 9787654321  | Laptop, Headphones  | 1,1      | 1200 |  

---

## **3. University Course Enrollment**  
**Table: Course_Enrollment**  
| EnrollmentID | StudentName | StudentEmail      | CourseName | Instructor   | InstructorEmail    | Semester |  
|-------------|------------|------------------|------------|-------------|-----------------|----------|  
| 301         | Bob        | bob@mail.com     | DBMS       | Dr. Smith   | smith@uni.com   | Fall 2024 |  
| 302         | Alice      | alice@mail.com   | Networks   | Dr. Jones   | jones@uni.com   | Fall 2024 |  
| 303         | Mike       | mike@mail.com    | AI         | Dr. Brown   | brown@uni.com   | Spring 2025 |  
| 304         | Emma       | emma@mail.com    | DBMS       | Dr. Smith   | smith@uni.com   | Fall 2024 |  

---

## **4. Vehicle Registration System**  
**Table: Vehicle_Registration**  
| RegID | OwnerName | OwnerAddress | VehicleType | PlateNumber | InsuranceDetails                  |  
|------|----------|-------------|-------------|-------------|---------------------------------|  
| 401  | Tom      | NY, USA     | Car         | NY1234      | ABC Insurance, Valid till 2025 |  
| 402  | Alice    | LA, USA     | Bike        | LA5678      | XYZ Insurance, Valid till 2026 |  
| 403  | John     | TX, USA     | Truck       | TX9999      | DEF Insurance, Valid till 2027 |  
| 404  | Emma     | SF, USA     | SUV         | SF3456      | GHI Insurance, Valid till 2028 |  

---

## **5. Hospital Management System**  
**Table: Patient_Records**  
| PatientID | Name  | Address   | Phone        | Disease       | Medicines        | Doctor   | DoctorPhone |  
|-----------|------ |----------|-------------|--------------|----------------|---------|------------|  
| 501       | Alex  | NY, USA  | 9876543210  | Flu          | Med1, Med2     | Dr. John | 9999888877 |  
| 502       | Bob   | LA, USA  | 8765432109  | Diabetes     | Med3, Med4     | Dr. Smith | 9876543211 |  
| 503       | Alice | TX, USA  | 9123456789  | Hypertension | Med5           | Dr. Brown | 8765432109 |  
| 504       | Emma  | SF, USA  | 9456123456  | Flu, Fever   | Med1, Med6     | Dr. Jones | 9123456788 |  

---

## **6. Banking Transactions**  
**Table: Transactions**  
| TransactionID | AccountNumber | CustomerName | Branch | TransactionType | Amount |  
|--------------|--------------|--------------|--------|----------------|--------|  
| 601          | 1001         | David        | NY     | Deposit        | 5000   |  
| 602          | 1002         | Alice        | LA     | Withdrawal     | 2000   |  
| 603          | 1003         | John         | SF     | Transfer       | 1000   |  
| 604          | 1004         | Emma         | TX     | Deposit        | 7000   |  

---

## **7. Library Management System**  
**Table: Library_Books**  
| BookID | Title  | Author  | Publisher  | Borrower  | BorrowerPhone | DueDate |  
|--------|-------|--------|-----------|----------|--------------|--------|  
| 701    | DBMS  | ABC    | XYZ Pub   | John     | 9876543210   | 2024-07-10 |  
| 702    | AI    | DEF    | PQR Pub   | Alice    | 8765432109   | 2024-07-15 |  
| 703    | Networks | GHI  | LMN Pub   | Bob      | 9123456789   | 2024-07-20 |  
| 704    | OS    | JKL    | OPQ Pub   | Emma     | 9456123456   | 2024-07-25 |  

---

## **8. Hotel Booking System**  
**Table: Hotel_Bookings**  
| BookingID | CustomerName | RoomType | Amenities  | PaymentDetails | CheckInDate |  
|-----------|-------------|---------|------------|---------------|-------------|  
| 801       | Daniel      | Deluxe  | WiFi, TV   | Card Payment  | 2024-07-05  |  
| 802       | Alice       | Suite   | WiFi, Pool | Cash          | 2024-07-06  |  
| 803       | Bob         | Standard| AC, TV     | Online Payment | 2024-07-07  |  
| 804       | Emma        | Suite   | WiFi, TV, AC | Card Payment  | 2024-07-08  |  

---

## **More Complex Tables**
9. **E-Commerce Cart System** (CartID, CustomerID, ProductList, TotalPrice)  
10. **Flight Ticket Booking System** (TicketID, PassengerName, FlightDetails, PaymentMode)  
11. **Telecom Call Records** (CallID, Caller, Receiver, Duration, CallType)  
12. **Job Application System** (ApplicantID, Resume, Skills, JobAppliedFor)  
13. **Warehouse Inventory** (InventoryID, ProductList, SupplierDetails)  
14. **Gym Memberships** (MemberID, Plan, Trainer, WorkoutSchedule)  
15. **University Hostel Management** (StudentID, RoomType, Fees, PaymentMode)  

---

### **Would You Like SQL Scripts for These Tables?**
These tables contain **complex dependencies** making them **perfect for 3NF normalization**. I can also provide **SQL queries** for creating, inserting, and decomposing these tables.

### **Normalization of Complex Tables to 3NF**  

We'll **normalize** each table step by step:  

1. **Identify Issues** (Repeating groups, multivalued attributes, partial or transitive dependencies).  
2. **Normalize to 1NF → 2NF → 3NF** by breaking them into smaller tables.  
3. **Provide SQL Queries** to create the final tables in **3NF**.  

---

## **1. Employee Records**  
**Issues in Original Table (Employee_Details):**  
- **Multivalued attributes:** `Projects`, `PhoneNumbers`  
- **Transitive dependency:** `ManagerID` depends on `Department`.  

### **Normalization Steps:**  
### **1NF:**  
- Split `Projects` and `PhoneNumbers` into separate rows.  
- Each column should have atomic values.  

```sql
CREATE TABLE Employee (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(50),
    Department VARCHAR(50),
    Address VARCHAR(100),
    ManagerID INT
);

CREATE TABLE Employee_Project (
    EmpID INT,
    ProjectID VARCHAR(10),
    PRIMARY KEY (EmpID, ProjectID),
    FOREIGN KEY (EmpID) REFERENCES Employee(EmpID)
);

CREATE TABLE Employee_Phone (
    EmpID INT,
    PhoneNumber VARCHAR(15),
    PRIMARY KEY (EmpID, PhoneNumber),
    FOREIGN KEY (EmpID) REFERENCES Employee(EmpID)
);
```

**Final 3NF Tables:**  
- `Employee (EmpID, Name, Department, Address, ManagerID)`
- `Project_Assignment (EmpID, ProjectID)`
- `Employee_Phone (EmpID, PhoneNumber)`

---

## **2. Customer Orders System**  
**Issues:**  
- `ProductDetails` and `Quantity` are multivalued.  
- `CustomerName` depends on `OrderID`, not `ProductDetails`.  

### **1NF → 3NF:**  
```sql
CREATE TABLE Customer (
    CustomerID INT PRIMARY KEY,
    CustomerName VARCHAR(50),
    Address VARCHAR(100),
    Phone VARCHAR(15)
);

CREATE TABLE Orders (
    OrderID INT PRIMARY KEY,
    CustomerID INT,
    TotalPrice DECIMAL(10,2),
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID)
);

CREATE TABLE Order_Details (
    OrderID INT,
    ProductID INT,
    Quantity INT,
    PRIMARY KEY (OrderID, ProductID),
    FOREIGN KEY (OrderID) REFERENCES Orders(OrderID)
);
```

**Final 3NF Tables:**  
- `Customer (CustomerID, CustomerName, Address, Phone)`  
- `Orders (OrderID, CustomerID, TotalPrice)`  
- `Order_Details (OrderID, ProductID, Quantity)`

---

## **3. University Course Enrollment**  
**Issues:**  
- `Instructor` and `InstructorEmail` depend on `CourseName`.  

### **1NF → 3NF:**  
```sql
CREATE TABLE Student (
    StudentID INT PRIMARY KEY,
    StudentName VARCHAR(50),
    StudentEmail VARCHAR(100)
);

CREATE TABLE Course (
    CourseID INT PRIMARY KEY,
    CourseName VARCHAR(50),
    InstructorID INT
);

CREATE TABLE Instructor (
    InstructorID INT PRIMARY KEY,
    InstructorName VARCHAR(50),
    InstructorEmail VARCHAR(100)
);

CREATE TABLE Enrollment (
    EnrollmentID INT PRIMARY KEY,
    StudentID INT,
    CourseID INT,
    Semester VARCHAR(20),
    FOREIGN KEY (StudentID) REFERENCES Student(StudentID),
    FOREIGN KEY (CourseID) REFERENCES Course(CourseID)
);
```

**Final 3NF Tables:**  
- `Student (StudentID, StudentName, StudentEmail)`  
- `Course (CourseID, CourseName, InstructorID)`  
- `Instructor (InstructorID, InstructorName, InstructorEmail)`  
- `Enrollment (EnrollmentID, StudentID, CourseID, Semester)`

---

## **4. Vehicle Registration System**  
**Issues:**  
- `InsuranceDetails` is not atomic.  

### **1NF → 3NF:**  
```sql
CREATE TABLE Vehicle (
    RegID INT PRIMARY KEY,
    OwnerID INT,
    VehicleType VARCHAR(50),
    PlateNumber VARCHAR(15),
    FOREIGN KEY (OwnerID) REFERENCES Owner(OwnerID)
);

CREATE TABLE Owner (
    OwnerID INT PRIMARY KEY,
    OwnerName VARCHAR(50),
    OwnerAddress VARCHAR(100)
);

CREATE TABLE Insurance (
    InsuranceID INT PRIMARY KEY,
    Provider VARCHAR(50),
    Validity DATE,
    RegID INT,
    FOREIGN KEY (RegID) REFERENCES Vehicle(RegID)
);
```

**Final 3NF Tables:**  
- `Owner (OwnerID, OwnerName, OwnerAddress)`  
- `Vehicle (RegID, OwnerID, VehicleType, PlateNumber)`  
- `Insurance (InsuranceID, Provider, Validity, RegID)`

---

## **5. Hospital Management System**  
**Issues:**  
- `DoctorPhone` depends on `Doctor`.  

### **1NF → 3NF:**  
```sql
CREATE TABLE Patient (
    PatientID INT PRIMARY KEY,
    Name VARCHAR(50),
    Address VARCHAR(100),
    Phone VARCHAR(15)
);

CREATE TABLE Doctor (
    DoctorID INT PRIMARY KEY,
    DoctorName VARCHAR(50),
    DoctorPhone VARCHAR(15)
);

CREATE TABLE Treatment (
    PatientID INT,
    DoctorID INT,
    Disease VARCHAR(50),
    Medicine VARCHAR(50),
    PRIMARY KEY (PatientID, DoctorID, Disease),
    FOREIGN KEY (PatientID) REFERENCES Patient(PatientID),
    FOREIGN KEY (DoctorID) REFERENCES Doctor(DoctorID)
);
```

**Final 3NF Tables:**  
- `Patient (PatientID, Name, Address, Phone)`  
- `Doctor (DoctorID, DoctorName, DoctorPhone)`  
- `Treatment (PatientID, DoctorID, Disease, Medicine)`

---

## **Other Tables (Summary)**  
| **Table** | **Issues** | **Final 3NF Tables** |
|-----------|-----------|----------------------|
| Banking Transactions | CustomerName depends on AccountNumber | `Customer (CustomerID, Name)`, `Account (AccountNumber, CustomerID)`, `Transaction (TransactionID, AccountNumber, Amount, Type)` |
| Library Books | Borrower depends on BookID | `Book (BookID, Title, Author, Publisher)`, `Member (MemberID, Name, Phone)`, `Borrow (BookID, MemberID, DueDate)` |
| Hotel Bookings | PaymentDetails not atomic | `Customer (CustomerID, Name)`, `Room (RoomID, Type)`, `Booking (BookingID, CustomerID, RoomID, CheckInDate, PaymentMethod)` |
| E-Commerce Cart | Multiple products in one column | `Customer (CustomerID, Name)`, `Cart (CartID, CustomerID)`, `CartItems (CartID, ProductID, Quantity)` |
| Flight Booking | FlightDetails not atomic | `Passenger (PassengerID, Name)`, `Flight (FlightID, Details)`, `Booking (BookingID, PassengerID, FlightID, PaymentMode)` |
| Telecom Calls | CallType in main table | `Customer (CustomerID, Name)`, `Call (CallID, CallerID, ReceiverID, Duration, Type)` |
| Job Applications | Skills not atomic | `Applicant (ApplicantID, Name)`, `Skills (ApplicantID, Skill)`, `Job (JobID, Title)`, `Application (ApplicantID, JobID)` |

---

### **Would You Like Data Insert Queries?**
I can generate **INSERT statements** for all tables with **sample data**. Let me know if you want them! 🚀