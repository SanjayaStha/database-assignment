
# CRUD Practice Questions

### **Question 1: Schema Definition**
Given the following schema, write a `CREATE TABLE` query:

**Table: Students**  
| Column Name     | Data Type          | Constraints                |  
|------------------|--------------------|----------------------------|  
| StudentID        | INT               | PRIMARY KEY, AUTO_INCREMENT|  
| FirstName        | VARCHAR(50)       | NOT NULL                   |  
| LastName         | VARCHAR(50)       | NOT NULL                   |  
| Age              | INT               | CHECK (Age >= 16)          |  
| EnrollmentDate   | DATE              | DEFAULT CURRENT_DATE       |  
| Major            | VARCHAR(100)      |                            |  

**Task**:  
Write the SQL query to create the above table.

---

### **Question 2: Insert Data**  
Insert the following rows into the **Students** table:  

| StudentID | FirstName | LastName  | Age | EnrollmentDate | Major           |  
|-----------|-----------|-----------|-----|----------------|-----------------|  
| 1         | Alice     | Johnson   | 18  | 2023-09-01     | Computer Science|  
| 2         | Bob       | Smith     | 20  | 2022-06-15     | Mathematics     |  
| 3         | Charlie   | Brown     | 19  | 2021-08-20     | Physics         |  
| 4         | Daisy     | Carter    | 21  | 2023-01-10     | Biology         |  
| 5         | Ethan     | Taylor    | 22  | 2023-03-25     | Chemistry       |  

**Task**:  
Write the `INSERT INTO` query to add these rows to the table.

---

### **Question 3: Update Data**  
Perform the following updates on the **Students** table:  

1. Change the major of the student with `StudentID = 1` to "Data Science".  
2. Increase the age of all students enrolled before "2023-01-01" by 1 year.  
3. Update the `LastName` of the student with `FirstName = 'Daisy'` to "Cooper".  
4. Set the `Major` to "Undeclared" for all students younger than 20.  
5. Update the `EnrollmentDate` of the student with `StudentID = 5` to "2024-01-01".  
6. Set the `Major` to "Physics" for all students whose current `Major` is "Biology".  
7. Update the `Age` to 23 for all students with `FirstName = 'Charlie'`.  
8. Change the `LastName` of the student with `Major = 'Mathematics'` to "Williams".  
9. Update the `FirstName` of the youngest student to "Alex".  
10. Set the `Age` to NULL for all students with `Major = 'Undeclared'`.  
11. Set the `Major` to `DBMS` for all youngest students.

**Task**:  
Write 10 separate `UPDATE` queries to perform the above operations.

---

### **Question 4: Delete Records**  
Perform the following deletions on the **Students** table:  

1. Delete the record of the student with `StudentID = 3`.  
2. Remove all students with the `Major` as "Undeclared".  
3. Delete all students who enrolled after "2023-01-01".  
4. Remove students who are older than 21.  
5. Delete the record of the student with `FirstName = 'Ethan'` and `LastName = 'Taylor'`.  
6. Delete all students with `Age = NULL`.  
7. Remove all students with `LastName` starting with the letter "C".  
8. Delete all students where `EnrollmentDate` is earlier than "2022-01-01".  
9. Remove all students who have "Physics" as their `Major`.  
10. Delete all records from the table without dropping the table itself.  

**Task**:  
Write 10 separate `DELETE` queries to perform the above deletions.


### **Question 1: Schema Definition**  
#### **Create Table Query:**
```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    FirstName VARCHAR(50) NOT NULL,
    LastName VARCHAR(50) NOT NULL,
    Age INT CHECK (Age >= 16),
    EnrollmentDate DATE DEFAULT CURRENT_DATE,
    Major VARCHAR(100)
);
```

---

### **Question 2: Insert Data**  
#### **Insert Queries:**
```sql
INSERT INTO Students (StudentID, FirstName, LastName, Age, EnrollmentDate, Major)
VALUES 
(1, 'Alice', 'Johnson', 18, '2023-09-01', 'Computer Science'),
(2, 'Bob', 'Smith', 20, '2022-06-15', 'Mathematics'),
(3, 'Charlie', 'Brown', 19, '2021-08-20', 'Physics'),
(4, 'Daisy', 'Carter', 21, '2023-01-10', 'Biology'),
(5, 'Ethan', 'Taylor', 22, '2023-03-25', 'Chemistry');
```

---

### **Question 3: Update Data**  
#### **Update Queries:**
1. Change the major of the student with `StudentID = 1` to "Data Science":
   ```sql
   UPDATE Students 
   SET Major = 'Data Science' 
   WHERE StudentID = 1;
   ```

2. Increase the age of all students enrolled before "2023-01-01" by 1 year:
   ```sql
   UPDATE Students 
   SET Age = Age + 1 
   WHERE EnrollmentDate < '2023-01-01';
   ```

3. Update the `LastName` of the student with `FirstName = 'Daisy'` to "Cooper":
   ```sql
   UPDATE Students 
   SET LastName = 'Cooper' 
   WHERE FirstName = 'Daisy';
   ```

4. Set the `Major` to "Undeclared" for all students younger than 20:
   ```sql
   UPDATE Students 
   SET Major = 'Undeclared' 
   WHERE Age < 20;
   ```

5. Update the `EnrollmentDate` of the student with `StudentID = 5` to "2024-01-01":
   ```sql
   UPDATE Students 
   SET EnrollmentDate = '2024-01-01' 
   WHERE StudentID = 5;
   ```

6. Set the `Major` to "Physics" for all students whose current `Major` is "Biology":
   ```sql
   UPDATE Students 
   SET Major = 'Physics' 
   WHERE Major = 'Biology';
   ```

7. Update the `Age` to 23 for all students with `FirstName = 'Charlie'`:
   ```sql
   UPDATE Students 
   SET Age = 23 
   WHERE FirstName = 'Charlie';
   ```

8. Change the `LastName` of the student with `Major = 'Mathematics'` to "Williams":
   ```sql
   UPDATE Students 
   SET LastName = 'Williams' 
   WHERE Major = 'Mathematics';
   ```

9. Update the `FirstName` of the youngest student to "Alex":
   ```sql
   UPDATE Students 
   SET FirstName = 'Alex' 
   WHERE Age = (SELECT MIN(Age) FROM Students);
   ```

10. Set the `Age` to NULL for all students with `Major = 'Undeclared'`:
    ```sql
    UPDATE Students 
    SET Age = NULL 
    WHERE Major = 'Undeclared';
    ```

---

### **Question 4: Delete Records**  
#### **Delete Queries:**
1. Delete the record of the student with `StudentID = 3`:
   ```sql
   DELETE FROM Students 
   WHERE StudentID = 3;
   ```

2. Remove all students with the `Major` as "Undeclared":
   ```sql
   DELETE FROM Students 
   WHERE Major = 'Undeclared';
   ```

3. Delete all students who enrolled after "2023-01-01":
   ```sql
   DELETE FROM Students 
   WHERE EnrollmentDate > '2023-01-01';
   ```

4. Remove students who are older than 21:
   ```sql
   DELETE FROM Students 
   WHERE Age > 21;
   ```

5. Delete the record of the student with `FirstName = 'Ethan'` and `LastName = 'Taylor'`:
   ```sql
   DELETE FROM Students 
   WHERE FirstName = 'Ethan' AND LastName = 'Taylor';
   ```

6. Delete all students with `Age = NULL`:
   ```sql
   DELETE FROM Students 
   WHERE Age IS NULL;
   ```

7. Remove all students with `LastName` starting with the letter "C":
   ```sql
   DELETE FROM Students 
   WHERE LastName LIKE 'C%';
   ```

8. Delete all students where `EnrollmentDate` is earlier than "2022-01-01":
   ```sql
   DELETE FROM Students 
   WHERE EnrollmentDate < '2022-01-01';
   ```

9. Remove all students who have "Physics" as their `Major`:
   ```sql
   DELETE FROM Students 
   WHERE Major = 'Physics';
   ```

10. Delete all records from the table without dropping the table itself:
    ```sql
    DELETE FROM Students;
    ```

11. Update the major to dbms for all youngest student
    ```sql
    UPDATE Students
    SET Major = 'Computer Science', Age = Age + 1
    WHERE Age = (SELECT MIN(Age) FROM Students);
    ```
---

