# **Module 1: Introduction to Databases**

---

## **1.1 What is a Database?**

### **Definition**  
A database is an organized collection of data that can be easily accessed, managed, and updated. It acts as a central repository for structured data to support efficient retrieval and manipulation.

### **Purpose of Databases**  
- **Data Storage**: Provides a systematic way to store large volumes of data.  
- **Data Retrieval**: Enables users to access data efficiently.  
- **Data Integrity**: Ensures the consistency and accuracy of data.  
- **Data Sharing**: Allows multiple users or applications to access the same data simultaneously.

### **Real-Life Examples**  
1. **E-commerce Websites**:  
   - Amazon stores product details, customer information, and order histories in databases.  
2. **Healthcare Systems**:  
   - Hospitals maintain patient records, doctor schedules, and billing in databases.  
3. **Social Media Platforms**:  
   - Platforms like Facebook and Instagram store user profiles, posts, and connections.

### **Sample Use Case**  
A **library system** database might include:  
- **Books Table**:  
  - Columns: BookID, Title, Author, Genre, AvailableCopies.  
- **Members Table**:  
  - Columns: MemberID, Name, ContactInfo, MembershipDate.  
- **Borrowing Table**:  
  - Columns: BorrowID, BookID, MemberID, BorrowDate, ReturnDate.

---

## **1.2 Database Management System (DBMS)**

### **Definition**  
A DBMS is a software system that allows users to define, create, maintain, and control access to a database.

### **Functions of a DBMS**  
1. **Data Storage and Retrieval**: Efficiently stores and retrieves large volumes of data.  
2. **Data Manipulation**: Supports querying, updating, and deleting data.  
3. **Data Security**: Controls user access to ensure data confidentiality and integrity.  
4. **Concurrency Control**: Manages simultaneous data access by multiple users.  
5. **Backup and Recovery**: Ensures data recovery in case of system failure.

### **Advantages of a DBMS Over Traditional File Systems**  
- Eliminates redundancy and inconsistencies.  
- Provides a centralized management system for data.  
- Supports complex queries with minimal effort.  
- Enhances security and multi-user access.

### **Example**  
A DBMS like MySQL can manage:  
- A **banking system** where customer data, transactions, and account details are stored in different tables with relationships.

---

## **1.3 Types of Databases**

### **Relational Databases**  
- Organizes data in tables with rows and columns.  
- Uses SQL for data manipulation.  
- **Example**: MySQL, PostgreSQL.  

### **Non-Relational (NoSQL) Databases**  
- Stores unstructured or semi-structured data.  
- Suitable for handling large datasets.  
- **Example**: MongoDB, Cassandra.  

### **Distributed Databases**  
- Data is distributed across multiple locations.  
- Ensures availability and scalability.  
- **Example**: Google Spanner, Amazon DynamoDB.  

### **Cloud Databases**  
- Hosted on cloud platforms.  
- Offers flexibility, scalability, and cost-effectiveness.  
- **Example**: AWS RDS, Microsoft Azure SQL Database.

---

## **1.4 Database System Architecture**

### **Levels of Architecture**  
1. **Physical Level**:  
   - Describes how data is stored on storage devices.  
   - Example: Data blocks, records, indexes.  

2. **Logical Level**:  
   - Describes what data is stored and its relationships.  
   - Example: Tables, schemas, relationships.  

3. **View Level**:  
   - Provides user-specific data views.  
   - Example: Customer view, Manager view.

### **Schemas and Instances**  
- **Schema**: The overall structure of the database.  
  - Example: Database design with tables and relationships.  
- **Instance**: The data at a particular point in time.  
  - Example: Current records in a database table.

### **Example Architecture**  
A **university database** with:  
- **Physical Level**: Disk storage for student data.  
- **Logical Level**: Tables for Students, Courses, and Enrollments.  
- **View Level**:  
  - Admin view: Full access to data.  
  - Student view: Access to their own records only.

![alt text](image.png)