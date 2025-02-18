Here’s an explanation of **Functional Dependency**, **Partial Dependency**, and **Transitive Dependency** with examples in tabular form:

### 1. **Functional Dependency (FD)**

- **Definition**: A functional dependency occurs when one attribute (or set of attributes) determines another attribute.
- **Notation**: If attribute `A → B`, then `A` uniquely determines `B`.

**Example**: Consider the following table:

| StudentID | StudentName | CourseID | CourseName |
|-----------|-------------|----------|------------|
| S001      | John        | C101     | Physics    |
| S002      | Alice       | C102     | Math       |

In this table:
- `StudentID → StudentName`: The `StudentID` determines a unique `StudentName`. So, for every `StudentID`, there is exactly one `StudentName`.
- `CourseID → CourseName`: Similarly, `CourseID` determines a unique `CourseName`.

### 2. **Partial Dependency**

- **Definition**: A partial dependency occurs when a non-prime attribute depends on only a part of a composite primary key.
- **Notation**: If we have a composite primary key `(A, B)` and an attribute `C` depends on `A` but not on `B`, it is a partial dependency.

**Example**: Consider the following table with a composite primary key `(StudentID, CourseID)`:

| StudentID | CourseID | StudentName | CourseName |
|-----------|----------|-------------|------------|
| S001      | C101     | John        | Physics    |
| S002      | C102     | Alice       | Math       |

Here, the composite primary key is `(StudentID, CourseID)`. 
- `StudentID → StudentName`: The `StudentID` determines the `StudentName`, but this dependency is based only on `StudentID`, not the whole composite key.
- `CourseID → CourseName`: Similarly, `CourseID` determines `CourseName`.

These are partial dependencies because they depend only on a part of the composite key (`StudentID` or `CourseID`), not the entire key `(StudentID, CourseID)`.

### 3. **Transitive Dependency**

- **Definition**: A transitive dependency occurs when an attribute depends on another attribute through a third attribute. In other words, if `A → B` and `B → C`, then `A → C` is a transitive dependency.
  
**Example**: Consider the following table:

| EmployeeID | EmployeeName | Department  | DepartmentHead |
|------------|--------------|-------------|----------------|
| E001       | Bob          | Sales       | Tom            |
| E002       | Alice        | IT          | Jerry          |

Here:
- `EmployeeID → EmployeeName`: `EmployeeID` determines `EmployeeName`.
- `Department → DepartmentHead`: `Department` determines `DepartmentHead`.

Since `EmployeeID → Department` (via some relation between employees and departments), and `Department → DepartmentHead`, we can say `EmployeeID → DepartmentHead` is a **transitive dependency**.

In this case, `EmployeeID` indirectly determines the `DepartmentHead` through the `Department`, which violates the rule of normalization (i.e., 3NF), where there should be no transitive dependencies.

---

### Summary:

| **Type of Dependency**   | **Example**                                            | **Explanation**                                        |
|--------------------------|--------------------------------------------------------|--------------------------------------------------------|
| **Functional Dependency (FD)** | `StudentID → StudentName`                            | One attribute determines another uniquely.              |
| **Partial Dependency**    | `StudentID → StudentName` (when `StudentID, CourseID` is the composite key) | Non-prime attribute depends on part of the composite key. |
| **Transitive Dependency** | `EmployeeID → DepartmentHead` (via `Department`)        | One attribute depends on another through a third attribute. |


Here are 10 more examples of **functional**, **partial**, and **transitive dependencies** to deepen your understanding of these concepts:

---

### **Example 1: Functional Dependency**

**Relation:** `Product(ProductID, ProductName, Category, Price, SupplierID)`

**Functional Dependencies:**
- `ProductID → ProductName, Category, Price, SupplierID`

**Explanation:**
- The **ProductID** uniquely determines the **ProductName**, **Category**, **Price**, and **SupplierID**. If you know the **ProductID**, you can always find the corresponding details for the product.

---

### **Example 2: Partial Dependency**

**Relation:** `OrderDetails(OrderID, ProductID, Quantity, ProductName, ProductPrice)`

**Functional Dependencies:**
- `OrderID, ProductID → Quantity, ProductName, ProductPrice`
- `ProductID → ProductName, ProductPrice` (Partial Dependency)

**Explanation:**
- **ProductID → ProductName, ProductPrice** is a **partial dependency** because **ProductID** determines the **ProductName** and **ProductPrice**, but these attributes are dependent on just part of the composite primary key (the **ProductID**) rather than the full key (**OrderID, ProductID**).

---

### **Example 3: Transitive Dependency**

**Relation:** `Employee(EmployeeID, EmployeeName, DepartmentID, DepartmentName, DepartmentHead)`

**Functional Dependencies:**
- `EmployeeID → EmployeeName, DepartmentID`
- `DepartmentID → DepartmentName, DepartmentHead`

**Explanation:**
- **DepartmentName** and **DepartmentHead** are **transitively dependent** on **EmployeeID** because **EmployeeID** determines **DepartmentID**, and **DepartmentID** in turn determines **DepartmentName** and **DepartmentHead**.

---

### **Example 4: Mixed Dependencies**

**Relation:** `Library(BookID, Title, AuthorID, AuthorName, PublisherName, PublisherLocation)`

**Functional Dependencies:**
- `BookID → Title, AuthorID, PublisherName`
- `AuthorID → AuthorName`
- `PublisherName → PublisherLocation`

**Explanation:**
- **AuthorName** is **transitively dependent** on **BookID** through **AuthorID**, and **PublisherLocation** is **transitively dependent** on **BookID** through **PublisherName**.

---

### **Example 5: Functional Dependency**

**Relation:** `CustomerOrder(CustomerID, OrderID, OrderDate, ProductID, Quantity, TotalPrice)`

**Functional Dependencies:**
- `OrderID → CustomerID, OrderDate, ProductID, Quantity, TotalPrice`

**Explanation:**
- The **OrderID** uniquely determines all the other attributes (e.g., **CustomerID**, **OrderDate**, etc.) in the relation. Knowing the **OrderID** lets you determine all other attributes for that order.

---

### **Example 6: Partial Dependency**

**Relation:** `CourseRegistration(StudentID, CourseID, InstructorID, InstructorName, Credits)`

**Functional Dependencies:**
- `StudentID, CourseID → InstructorID, Credits`
- `InstructorID → InstructorName` (Partial Dependency)

**Explanation:**
- **InstructorID → InstructorName** is a **partial dependency** because **InstructorName** depends only on **InstructorID**, not the full composite key (**StudentID, CourseID**).

---

### **Example 7: Transitive Dependency**

**Relation:** `Project(EmployeeID, ProjectID, ProjectName, ManagerID, ManagerName)`

**Functional Dependencies:**
- `EmployeeID, ProjectID → ProjectName, ManagerID`
- `ManagerID → ManagerName`

**Explanation:**
- **ManagerName** is **transitively dependent** on **EmployeeID** through **ManagerID**. That is, **EmployeeID → ManagerID** and **ManagerID → ManagerName**.

---

### **Example 8: Partial and Transitive Dependency**

**Relation:** `OrderDetails(OrderID, ProductID, ProductName, ProductPrice, SupplierID, SupplierName)`

**Functional Dependencies:**
- `OrderID, ProductID → ProductName, ProductPrice, SupplierID`
- `SupplierID → SupplierName` (Transitive Dependency)

**Explanation:**
- The relation contains a **transitive dependency**: **SupplierName** is transitively dependent on **OrderID** via **SupplierID**.

---

### **Example 9: Functional Dependency**

**Relation:** `Supplier(SupplierID, SupplierName, SupplierLocation, ContactPerson, ContactNumber)`

**Functional Dependencies:**
- `SupplierID → SupplierName, SupplierLocation, ContactPerson, ContactNumber`

**Explanation:**
- The **SupplierID** uniquely determines **SupplierName**, **SupplierLocation**, **ContactPerson**, and **ContactNumber**. Knowing the **SupplierID**, you can find all the other attributes related to that supplier.

---

### **Example 10: Transitive Dependency**

**Relation:** `StudentEnrollment(StudentID, CourseID, InstructorID, InstructorName, CourseName)`

**Functional Dependencies:**
- `StudentID, CourseID → InstructorID, CourseName`
- `InstructorID → InstructorName`

**Explanation:**
- **InstructorName** is **transitively dependent** on **StudentID, CourseID** because **InstructorID** is dependent on **StudentID, CourseID**, and **InstructorID** in turn determines **InstructorName**.

---

These examples highlight how **functional**, **partial**, and **transitive dependencies** manifest in database relations. Understanding these dependencies is crucial for database design and normalization.