# **Module 3: Relational Database Concepts**

---

## **3.1 Relational Model Overview**

### **Structure of Relational Databases**
Relational databases organize data into tables (relations), where each table consists of rows (tuples) and columns (attributes).  
- **Tables**: Represent entities.  
  - **Example**: A `Students` table stores information about students.  
- **Rows**: Represent individual records in the table.  
  - **Example**: A row in `Students` represents a single student.  
- **Columns**: Represent attributes of the entity.  
  - **Example**: Columns in `Students` could be `StudentID`, `Name`, `Email`.

**Example Table**:  
| StudentID | Name       | Email              | Age |  
|-----------|------------|--------------------|-----|  
| 1         | Alice Wong | alice@example.com  | 20  |  
| 2         | Bob Smith  | bob@example.com    | 22  |  

---

### **Relational Algebra Basics**
Relational algebra is a formal language for manipulating relational data. Common operations include:  
1. **Selection (σ)**: Filters rows based on conditions.  
   - **Example**: `σ(Age > 20)(Students)` retrieves students older than 20.  
2. **Projection (π)**: Selects specific columns.  
   - **Example**: `π(Name, Email)(Students)` retrieves only `Name` and `Email`.  
3. **Join (⋈)**: Combines related rows from two tables.  
   - **Example**: `Students ⋈ Courses` combines student and course information.  
4. **Union (∪)**: Combines rows from two tables with the same structure.  
5. **Intersection (∩)**: Retrieves rows present in both tables.  
6. **Difference (-)**: Retrieves rows present in one table but not the other.  

---

## **3.2 Keys and Constraints**

### **Primary Keys, Foreign Keys, and Unique Constraints**
- **Primary Key**: A unique identifier for each row.  
  - **Example**: `StudentID` in the `Students` table.  
- **Foreign Key**: A field in one table that links to the primary key in another table.  
  - **Example**: `CourseID` in the `Enrollments` table links to `Courses`.  
- **Unique Constraint**: Ensures values in a column are unique.  
  - **Example**: `Email` in the `Students` table.

**Example**:  
`Students` Table:  
| StudentID | Name       | Email              |  
|-----------|------------|--------------------|  
| 1         | Alice Wong | alice@example.com  |  

`Enrollments` Table:  
| EnrollmentID | StudentID | CourseID |  
|--------------|-----------|----------|  
| 1            | 1         | 101      |  

### **Referential Integrity**
- Ensures consistency between related tables using foreign keys.  
- **Example**: If `StudentID` 1 exists in `Students`, it must exist in `Enrollments`.

---

## **3.3 Normalization**

### **Definition and Importance**
Normalization is the process of organizing a database to minimize redundancy and dependency.  
- Reduces data anomalies during insert, update, or delete operations.  
- Improves data integrity and query performance.

### **Forms of Normalization**
1. **First Normal Form (1NF)**:  
   - Ensures each column contains atomic (indivisible) values.  
   - **Example**: Split a column storing multiple phone numbers into separate rows.  

2. **Second Normal Form (2NF)**:  
   - Achieves 1NF and removes partial dependency (non-key attributes depend on part of a composite key).  
   - **Example**: Move `CourseName` from `Enrollments` to `Courses` if it depends on `CourseID`.

3. **Third Normal Form (3NF)**:  
   - Achieves 2NF and removes transitive dependency (non-key attributes depend on other non-key attributes).  
   - **Example**: Move `InstructorName` to a separate table if it depends on `CourseID`.

4. **Boyce-Codd Normal Form (BCNF)**:  
   - A stricter version of 3NF, ensuring every determinant is a candidate key.  
   - **Example**: Address cases where a table has overlapping candidate keys.

---

### **Practical Example of Normalization**
#### **Unnormalized Table (UNF)**  
| StudentID | Name       | Courses            | Instructor  |  
|-----------|------------|--------------------|-------------|  
| 1         | Alice Wong | Math, Science      | Dr. Lee     |  
| 2         | Bob Smith  | Math, History      | Dr. Lee     |  

#### **1NF**  
| StudentID | Name       | Course     | Instructor  |  
|-----------|------------|------------|-------------|  
| 1         | Alice Wong | Math       | Dr. Lee     |  
| 1         | Alice Wong | Science    | Dr. Lee     |  

#### **2NF**  
**Courses Table**:  
| CourseID | Course     | Instructor  |  
|----------|------------|-------------|  
| 101      | Math       | Dr. Lee     |  
| 102      | Science    | Dr. Lee     |  

**Enrollments Table**:  
| EnrollmentID | StudentID | CourseID |  
|--------------|-----------|----------|  
| 1            | 1         | 101      |  
| 2            | 1         | 102      |  

#### **3NF**  
**Instructors Table**:  
| InstructorID | Instructor  |  
|--------------|-------------|  
| 1            | Dr. Lee     |  

**Courses Table**:  
| CourseID | Course     | InstructorID |  
|----------|------------|--------------|  
| 101      | Math       | 1            |  
| 102      | Science    | 1            |  
