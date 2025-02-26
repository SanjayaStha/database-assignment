
---

## **1️⃣ Entities & Their Relationships**
Based on the scenario, the following main **entities** (tables) are required:

1. **Branch** (X Hotel has multiple branches)  
2. **Manager** (Each branch has a manager)  
3. **Room** (Different types of rooms in each branch)  
4. **Customer** (Customers must register before booking)  
5. **Reservation** (Customers can book multiple rooms in a single reservation)  
6. **Invoice** (Generated when payment is made)  
7. **Review** (Customers leave ratings after their stay)  

---

## **2️⃣ ER Diagram**  

Here is a **simplified representation of the ER diagram:**  

```
[Branch] ← (1) --- (1) → [Manager]  
[Branch] ← (1) --- (M) → [Room]  
[Customer] ← (1) --- (M) → [Reservation] ← (M) --- (M) → [Room]  
[Reservation] ← (1) --- (1) → [Invoice]  
[Customer] ← (1) --- (M) → [Review] ← (1) --- (1) → [Branch]  
```
✅ **Legend:**  
- **(1) --- (M)** means **One-to-Many** relationship  
- **(M) --- (M)** means **Many-to-Many** relationship  

---

## **3️⃣ Tables and Attributes**
Now, let’s define the necessary **tables and attributes**:

### **🔹 Branch Table**
Stores **hotel branch details**.  
```sql
CREATE TABLE Branch (
    BranchID INT PRIMARY KEY AUTO_INCREMENT,  -- Unique identifier for each branch
    BranchName VARCHAR(100) NOT NULL,         -- Name of the branch
    Location VARCHAR(255) NOT NULL,           -- Address or city where branch is located
    ContactNumber VARCHAR(15) NOT NULL        -- Contact number for the branch
);
```
✅ Helps manage **different branches**.

---

### **🔹 Manager Table**
Stores **branch manager details**.  
```sql
CREATE TABLE Manager (
    ManagerID INT PRIMARY KEY AUTO_INCREMENT, -- Unique identifier for each manager
    FirstName VARCHAR(50) NOT NULL,           -- Manager's first name
    LastName VARCHAR(50) NOT NULL,            -- Manager's last name
    Email VARCHAR(100) UNIQUE NOT NULL,       -- Unique email for internal communication
    Phone VARCHAR(15),                         -- Contact number
    BranchID INT,                              -- Foreign key linking to the Branch
    FOREIGN KEY (BranchID) REFERENCES Branch(BranchID) ON DELETE SET NULL
);
```
✅ Links **each manager** to **one branch**.

---

### **🔹 Room Table**
Stores **room details** for each branch.  
```sql
CREATE TABLE Room (
    RoomID INT PRIMARY KEY AUTO_INCREMENT,   -- Unique room identifier
    BranchID INT,                            -- Foreign key linking to the branch
    RoomType ENUM('Standard Double', 'Standard Twin', 'Deluxe Double') NOT NULL,  
    Capacity INT NOT NULL,                    -- Number of guests the room can accommodate
    RoomRate DECIMAL(10,2) NOT NULL,          -- Price per night
    AvailabilityStatus BOOLEAN DEFAULT TRUE,  -- Room availability (True = available)
    FOREIGN KEY (BranchID) REFERENCES Branch(BranchID) ON DELETE CASCADE
);
```
✅ Helps manage **room types & availability** per **branch**.

---

### **🔹 Customer Table**
Stores **registered customers**.  
```sql
CREATE TABLE Customer (
    CustomerID INT PRIMARY KEY AUTO_INCREMENT,  
    FirstName VARCHAR(50) NOT NULL,             
    LastName VARCHAR(50) NOT NULL,              
    Email VARCHAR(100) UNIQUE NOT NULL,         -- Prevents duplicate registration
    ContactNumber VARCHAR(15) NOT NULL,         
    MailingAddress TEXT                         
);
```
✅ Ensures **unique customer registration** (no duplicate emails).  

---

### **🔹 Reservation Table**
Stores **room booking details**.  
```sql
CREATE TABLE Reservation (
    ReservationID INT PRIMARY KEY AUTO_INCREMENT,  
    CustomerID INT,                                 
    BranchID INT,                                   
    BookingDate DATE NOT NULL,                      -- When the booking was made
    CheckInDate DATE NOT NULL,                      
    CheckOutDate DATE NOT NULL,                     
    EmergencyContact VARCHAR(15),                   
    SpecialRequests TEXT,                           -- Late check-in, non-smoking, etc.
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID) ON DELETE CASCADE,
    FOREIGN KEY (BranchID) REFERENCES Branch(BranchID) ON DELETE CASCADE
);
```
✅ **Each reservation is linked** to **a single branch**.  
✅ **Special requests** stored as **text**.

---

### **🔹 Reservation_Room (Many-to-Many Relationship)**
Stores **rooms reserved in each booking**.  
```sql
CREATE TABLE Reservation_Room (
    ReservationID INT,  
    RoomID INT,        
    PRIMARY KEY (ReservationID, RoomID),
    FOREIGN KEY (ReservationID) REFERENCES Reservation(ReservationID) ON DELETE CASCADE,
    FOREIGN KEY (RoomID) REFERENCES Room(RoomID) ON DELETE CASCADE
);
```
✅ A **single booking** can include **multiple rooms**.

---

### **🔹 Invoice Table**
Stores **payment and billing details**.  
```sql
CREATE TABLE Invoice (
    InvoiceID INT PRIMARY KEY AUTO_INCREMENT,  
    ReservationID INT,                          
    TotalAmount DECIMAL(10,2) NOT NULL,        -- Total payment made by the customer
    PaymentDate DATE NOT NULL,                 
    FOREIGN KEY (ReservationID) REFERENCES Reservation(ReservationID) ON DELETE CASCADE
);
```
✅ **Each reservation has one invoice** after payment.

---

### **🔹 Review Table**
Stores **customer reviews & ratings**.  
```sql
CREATE TABLE Review (
    ReviewID INT PRIMARY KEY AUTO_INCREMENT,  
    CustomerID INT,                            
    BranchID INT,                              
    Rating INT CHECK (Rating BETWEEN 1 AND 5), -- Rating from 1 (Very Dissatisfied) to 5 (Very Satisfied)
    ReviewText TEXT,                           -- Optional text feedback
    ReviewDate TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    FOREIGN KEY (CustomerID) REFERENCES Customer(CustomerID) ON DELETE CASCADE,
    FOREIGN KEY (BranchID) REFERENCES Branch(BranchID) ON DELETE CASCADE
);
```
✅ Ensures **customer feedback** for **each branch**.

---

## **4️⃣ Summary of Relations**
| **Table** | **Key Relation** |
|-----------|----------------|
| `Branch` → `Manager` | **1-to-1** (Each branch has one manager) |
| `Branch` → `Room` | **1-to-Many** (A branch has multiple rooms) |
| `Customer` → `Reservation` | **1-to-Many** (A customer can book multiple times) |
| `Reservation` → `Room` | **Many-to-Many** (A reservation can include multiple rooms) |
| `Reservation` → `Invoice` | **1-to-1** (One invoice per reservation) |
| `Customer` → `Review` | **1-to-Many** (A customer can leave multiple reviews) |

---