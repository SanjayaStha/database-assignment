# **Module 2: Data Modeling and Database Design**

---

## **2.1 Data Modeling Concepts**

### **Entities, Attributes, and Relationships**  
- **Entities**: Objects or concepts that store data in a database.  
  - **Example**: In a library system, entities could be `Books`, `Members`, and `Borrowing`.  
- **Attributes**: Characteristics or properties of an entity.  
  - **Example**: The `Books` entity might have attributes: `BookID`, `Title`, `Author`, `Genre`.  
- **Relationships**: Associations between entities.  
  - **Example**: A `Borrowing` entity relates `Members` to `Books`.

---

### **Primary Key, Foreign Key, and Composite Key**  
- **Primary Key**: A unique identifier for each record in a table.  
  - **Example**: `BookID` in the `Books` table.  
- **Foreign Key**: An attribute in one table that links to the primary key of another table.  
  - **Example**: `MemberID` in `Borrowing` is a foreign key referencing `Members`.  
- **Composite Key**: A combination of two or more attributes that uniquely identifies a record.  
  - **Example**: `BorrowID` could be a composite of `BookID` and `MemberID`.

---

## **2.2 Entity-Relationship Diagrams (ERD)**

### **Components of an ERD**  
1. **Entities**: Represented as rectangles.  
   - Example: `Books`, `Members`, `Borrowing`.  
2. **Attributes**: Represented as ovals connected to entities.  
   - Example: `Title` for `Books`.  
3. **Relationships**: Represented as diamonds between entities.  
   - Example: A diamond labeled `Borrows` between `Members` and `Books`.  
4. **Keys**: Denoted with underlined attributes.  
   - Example: `BookID` is underlined in `Books`.

---

### **Cardinality and Participation**  
- **Cardinality**: Defines the number of instances in one entity that can be associated with instances in another.  
  - **One-to-One (1:1)**: Each member has exactly one membership card.  
  - **One-to-Many (1:N)**: A member can borrow multiple books, but each book is borrowed by one member at a time.  
  - **Many-to-Many (M:N)**: Students enroll in multiple courses, and courses have multiple students.  
- **Participation**: Defines whether all instances of an entity are involved in a relationship.  
  - **Total Participation**: All instances must participate (e.g., all members must borrow at least one book).  
  - **Partial Participation**: Some instances may not participate (e.g., not all books are borrowed).

---

## **2.3 Converting ERD to Relational Model**

### **Steps to Map ERD to Relational Tables**  
1. **Map Entities to Tables**:  
   - Each entity becomes a table.  
   - Example: `Books` entity becomes a `Books` table.  

2. **Map Attributes to Columns**:  
   - Each attribute of the entity becomes a column in the table.  
   - Example: `Books` table has columns `BookID`, `Title`, `Author`.  

3. **Map Relationships to Foreign Keys**:  
   - Add a foreign key in the table representing the dependent entity.  
   - Example: `Borrowing` table includes `MemberID` as a foreign key from `Members`.  

4. **Map Many-to-Many Relationships**:  
   - Create a new table for the relationship.  
   - Example: For `Students` and `Courses`, create an `Enrollment` table with `StudentID` and `CourseID`.

---

### **Integrity Constraints in Relational Models**  
1. **Primary Key Constraint**: Ensures each record has a unique identifier.  
   - Example: `BookID` in `Books`.  

2. **Foreign Key Constraint**: Ensures data consistency between related tables.  
   - Example: `MemberID` in `Borrowing` must match an existing `MemberID` in `Members`.  

3. **Unique Constraint**: Ensures a column has unique values.  
   - Example: `Email` in `Members` is unique.  

4. **Not Null Constraint**: Ensures a column cannot have null values.  
   - Example: `Title` in `Books` cannot be null.  

5. **Check Constraint**: Ensures values meet specific criteria.  
   - Example: `Rating` in `Reviews` must be between 1 and 5.

---

### **Example ERD Mapping**  

#### **Scenario**: Library Management System  
- **Entities**:  
  - `Books`: Attributes - `BookID`, `Title`, `Author`, `Genre`.  
  - `Members`: Attributes - `MemberID`, `Name`, `Email`, `Phone`.  
  - `Borrowing`: Attributes - `BorrowID`, `BookID`, `MemberID`, `BorrowDate`, `ReturnDate`.  

#### **Relational Tables**:  
1. **Books Table**:  
   - Columns: `BookID` (PK), `Title`, `Author`, `Genre`.  

2. **Members Table**:  
   - Columns: `MemberID` (PK), `Name`, `Email` (Unique), `Phone`.  

3. **Borrowing Table**:  
   - Columns: `BorrowID` (PK), `BookID` (FK), `MemberID` (FK), `BorrowDate`, `ReturnDate`.  
