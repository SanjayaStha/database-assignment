Here is a list of questions that guide students through the normalization process from **1NF** to **2NF** to **3NF**:

---

### **Question 1:**
Consider the relation `StudentMarks(StudentID, CourseID, Instructor, InstructorPhone, Marks)`.  
The functional dependencies are:
- `StudentID, CourseID → Marks`
- `CourseID → Instructor, InstructorPhone`

Is this relation in 1NF? If not, bring it to 1NF.  
Is it in 2NF? If not, bring it to 2NF.  
Is it in 3NF? If not, bring it to 3NF.

---

### **Question 2:**
Consider the relation `EmployeeDetails(EmpID, EmpName, EmpDept, DeptHead, DeptLocation)`.  
The functional dependencies are:
- `EmpID → EmpName, EmpDept`
- `EmpDept → DeptHead, DeptLocation`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 3:**
Consider the relation `BookDetails(BookID, BookTitle, Author, AuthorDOB, AuthorNationality)`.  
The functional dependencies are:
- `BookID → BookTitle, Author`
- `Author → AuthorDOB, AuthorNationality`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 4:**
Consider the relation `Sales(SaleID, ProductID, ProductName, ProductPrice, CustomerID, CustomerName)`.  
The functional dependencies are:
- `SaleID → ProductID, CustomerID`
- `ProductID → ProductName, ProductPrice`
- `CustomerID → CustomerName`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 5:**
Consider the relation `OrderDetails(OrderID, ProductID, Quantity, ProductPrice, CustomerID, CustomerName)`.  
The functional dependencies are:
- `OrderID → ProductID, Quantity`
- `ProductID → ProductPrice`
- `CustomerID → CustomerName`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 6:**
Consider the relation `StudentCourses(StudentID, CourseID, InstructorName, InstructorPhone)`.  
The functional dependencies are:
- `StudentID, CourseID → InstructorName`
- `InstructorName → InstructorPhone`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 7:**
Consider the relation `OrderInfo(OrderID, ProductID, ProductName, ProductPrice, CustomerID, CustomerName, CustomerPhone)`.  
The functional dependencies are:
- `OrderID → ProductID, CustomerID`
- `ProductID → ProductName, ProductPrice`
- `CustomerID → CustomerName, CustomerPhone`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 8:**
Consider the relation `StudentEnrollment(StudentID, CourseID, Instructor, InstructorEmail, CourseDuration)`.  
The functional dependencies are:
- `StudentID, CourseID → Instructor, CourseDuration`
- `Instructor → InstructorEmail`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 9:**
Consider the relation `HotelBooking(BookingID, CustomerID, HotelName, HotelLocation, CustomerPhone)`.  
The functional dependencies are:
- `BookingID → CustomerID, HotelName`
- `HotelName → HotelLocation`
- `CustomerID → CustomerPhone`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

### **Question 10:**
Consider the relation `ProductInventory(ProductID, ProductName, SupplierName, SupplierPhone, ProductQuantity)`.  
The functional dependencies are:
- `ProductID → ProductName, SupplierName, ProductQuantity`
- `SupplierName → SupplierPhone`

Is this relation in 1NF?  
Is it in 2NF?  
Is it in 3NF?

---

These questions will help students practice the normalization process step-by-step, moving from **1NF** to **2NF** and then to **3NF**.


Here are the answers with explanations for each of the normalization questions provided:

---

### **Question 1:**
Consider the relation `StudentMarks(StudentID, CourseID, Instructor, InstructorPhone, Marks)`.  
The functional dependencies are:
- `StudentID, CourseID → Marks`
- `CourseID → Instructor, InstructorPhone`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values (i.e., no repeating groups or multi-valued attributes).

#### **Is it in 2NF?**
**Answer:**  
No, it's not in **2NF** due to a **partial dependency**: `CourseID → Instructor, InstructorPhone`. These attributes depend only on part of the composite primary key (`CourseID`), not on the whole primary key (`StudentID, CourseID`).

#### **Convert to 2NF:**
1. **StudentMarks**: (`StudentID`, `CourseID`, `Marks`)  
   (The primary key is `StudentID, CourseID`.)
2. **CourseInfo**: (`CourseID`, `Instructor`, `InstructorPhone`)  
   (The primary key is `CourseID`.)

#### **Is it in 3NF?**
**Answer:**  
No, it's not in **3NF** due to a **transitive dependency**: `InstructorPhone` depends on `Instructor`, and `Instructor` depends on `CourseID`, which creates an indirect dependency from `CourseID` to `InstructorPhone`.

#### **Convert to 3NF:**
1. **StudentMarks**: (`StudentID`, `CourseID`, `Marks`)
2. **CourseInfo**: (`CourseID`, `Instructor`)
3. **InstructorInfo**: (`Instructor`, `InstructorPhone`)

Now, all non-key attributes depend directly on the primary key.

---

### **Question 2:**
Consider the relation `EmployeeDetails(EmpID, EmpName, EmpDept, DeptHead, DeptLocation)`.  
The functional dependencies are:
- `EmpID → EmpName, EmpDept`
- `EmpDept → DeptHead, DeptLocation`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
No, it's not in **2NF** because of a **partial dependency**: `EmpDept → DeptHead, DeptLocation`. `DeptHead` and `DeptLocation` depend only on `EmpDept`, not the entire primary key (`EmpID`, `EmpDept`).

#### **Convert to 2NF:**
1. **Employee**: (`EmpID`, `EmpName`, `EmpDept`)  
   (The primary key is `EmpID`.)
2. **Department**: (`EmpDept`, `DeptHead`, `DeptLocation`)  
   (The primary key is `EmpDept`.)

#### **Is it in 3NF?**
**Answer:**  
Yes, the relation is now in **3NF** because all non-key attributes are directly dependent on the primary key and there are no transitive dependencies.

---

### **Question 3:**
Consider the relation `BookDetails(BookID, BookTitle, Author, AuthorDOB, AuthorNationality)`.  
The functional dependencies are:
- `BookID → BookTitle, Author`
- `Author → AuthorDOB, AuthorNationality`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
No, it's not in **2NF** because of a **partial dependency**: `Author → AuthorDOB, AuthorNationality`. `AuthorDOB` and `AuthorNationality` depend only on `Author`, not the entire primary key (`BookID`, `Author`).

#### **Convert to 2NF:**
1. **Book**: (`BookID`, `BookTitle`, `Author`)  
   (The primary key is `BookID`, and `Author` is dependent on it.)
2. **AuthorInfo**: (`Author`, `AuthorDOB`, `AuthorNationality`)  
   (The primary key is `Author`.)

#### **Is it in 3NF?**
**Answer:**  
Yes, the relation is now in **3NF** because all non-key attributes are directly dependent on their respective primary keys, and there are no transitive dependencies.

---

### **Question 4:**
Consider the relation `Sales(SaleID, ProductID, ProductName, ProductPrice, CustomerID, CustomerName)`.  
The functional dependencies are:
- `SaleID → ProductID, CustomerID`
- `ProductID → ProductName, ProductPrice`
- `CustomerID → CustomerName`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
No, it’s not in **2NF** because of **partial dependencies**:
- `ProductID → ProductName, ProductPrice` (depends only on part of the primary key).
- `CustomerID → CustomerName` (depends only on part of the primary key).

#### **Convert to 2NF:**
1. **Sales**: (`SaleID`, `ProductID`, `CustomerID`)  
   (The primary key is `SaleID`.)
2. **Product**: (`ProductID`, `ProductName`, `ProductPrice`)  
   (The primary key is `ProductID`.)
3. **Customer**: (`CustomerID`, `CustomerName`)  
   (The primary key is `CustomerID`.)

#### **Is it in 3NF?**
**Answer:**  
Yes, the relations are now in **3NF** because all non-key attributes depend directly on their respective primary keys.

---

### **Question 5:**
Consider the relation `OrderDetails(OrderID, ProductID, Quantity, ProductPrice, CustomerID, CustomerName)`.  
The functional dependencies are:
- `OrderID → ProductID, Quantity`
- `ProductID → ProductPrice`
- `CustomerID → CustomerName`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
No, it’s not in **2NF** because of a **partial dependency**: `ProductID → ProductPrice`.

#### **Convert to 2NF:**
1. **OrderDetails**: (`OrderID`, `ProductID`, `Quantity`)  
   (The primary key is `OrderID`.)
2. **Product**: (`ProductID`, `ProductPrice`)  
   (The primary key is `ProductID`.)
3. **Customer**: (`CustomerID`, `CustomerName`)  
   (The primary key is `CustomerID`.)

#### **Is it in 3NF?**
Yes, the relations are now in **3NF** because there are no transitive dependencies.

---

### **Question 6:**
Consider the relation `StudentCourses(StudentID, CourseID, InstructorName, InstructorPhone)`.  
The functional dependencies are:
- `StudentID, CourseID → InstructorName`
- `InstructorName → InstructorPhone`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
Yes, the relation is in **2NF** because there are no partial dependencies.

#### **Is it in 3NF?**
**Answer:**  
No, it’s not in **3NF** because of the **transitive dependency**: `InstructorPhone` depends on `InstructorName`, which depends on the primary key (`StudentID, CourseID`).

#### **Convert to 3NF:**
1. **StudentCourses**: (`StudentID`, `CourseID`, `InstructorName`)
2. **InstructorInfo**: (`InstructorName`, `InstructorPhone`)

---

### **Question 7:**
Consider the relation `OrderInfo(OrderID, ProductID, ProductName, ProductPrice, CustomerID, CustomerName, CustomerPhone)`.  
The functional dependencies are:
- `OrderID → ProductID, CustomerID`
- `ProductID → ProductName, ProductPrice`
- `CustomerID → CustomerName, CustomerPhone`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
**Answer:**  
No, it’s not in **2NF** because of **partial dependencies**:
- `ProductID → ProductName, ProductPrice` (depends only on part of the composite key).
- `CustomerID → CustomerName, CustomerPhone` (depends only on part of the composite key).

#### **Convert to 2NF:**
1. **OrderInfo**: (`OrderID`, `ProductID`, `CustomerID`)
2. **Product**: (`ProductID`, `ProductName`, `ProductPrice`)
3. **Customer**: (`CustomerID`, `CustomerName`, `CustomerPhone`)

#### **Is it in 3NF?**
Yes, the relations are now in **3NF** because all non-key attributes depend directly on the primary key.

---

### **Question 8:**
Consider the relation `StudentEnrollment(StudentID, CourseID, Instructor, InstructorEmail, CourseDuration)`.  
The functional dependencies are:
- `StudentID, CourseID → Instructor, CourseDuration`
- `Instructor → InstructorEmail`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **

Is it in 2NF?**
Yes, the relation is in **2NF** because all non-key attributes are fully dependent on the primary key.

#### **Is it in 3NF?**
**Answer:**  
No, it's not in **3NF** because of a **transitive dependency**: `InstructorEmail` depends on `Instructor`, which depends on `StudentID, CourseID`.

#### **Convert to 3NF:**
1. **StudentEnrollment**: (`StudentID`, `CourseID`, `Instructor`, `CourseDuration`)
2. **InstructorInfo**: (`Instructor`, `InstructorEmail`)

---

### **Question 9:**
Consider the relation `HotelBooking(BookingID, CustomerID, HotelName, HotelLocation, CustomerPhone)`.  
The functional dependencies are:
- `BookingID → CustomerID, HotelName`
- `HotelName → HotelLocation`
- `CustomerID → CustomerPhone`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
Yes, the relation is in **2NF** because all non-key attributes depend fully on the primary key.

#### **Is it in 3NF?**
**Answer:**  
No, it’s not in **3NF** due to a **transitive dependency**: `HotelLocation` depends on `HotelName`, and `HotelName` depends on the primary key (`BookingID`).

#### **Convert to 3NF:**
1. **HotelBooking**: (`BookingID`, `CustomerID`, `HotelName`)
2. **HotelInfo**: (`HotelName`, `HotelLocation`)
3. **Customer**: (`CustomerID`, `CustomerPhone`)

---

### **Question 10:**
Consider the relation `ProductInventory(ProductID, ProductName, SupplierName, SupplierPhone, ProductQuantity)`.  
The functional dependencies are:
- `ProductID → ProductName, SupplierName, ProductQuantity`
- `SupplierName → SupplierPhone`

#### **Is this relation in 1NF?**
**Answer:**  
Yes, the relation is in **1NF** because all attributes have atomic values.

#### **Is it in 2NF?**
Yes, the relation is in **2NF** because all non-key attributes depend fully on the primary key.

#### **Is it in 3NF?**
**Answer:**  
No, it’s not in **3NF** due to a **transitive dependency**: `SupplierPhone` depends on `SupplierName`, and `SupplierName` depends on `ProductID`.

#### **Convert to 3NF:**
1. **ProductInventory**: (`ProductID`, `ProductName`, `SupplierName`, `ProductQuantity`)
2. **SupplierInfo**: (`SupplierName`, `SupplierPhone`)

---

These answers guide students through the normalization process from **1NF** to **3NF**.