Here is an updated version of the **Library System** practice set with **complex queries** that include multiple conditions:

---

### **1. Create Table Query**

 **Create a table named `Library` to store the following details:**
   - BookID (auto-incremented, primary key)
   - Title (varchar)
   - Author (varchar)
   - Publisher (varchar)
   - Genre (varchar)
   - PublishedYear (integer)
   - ISBN (varchar, unique)
   - Pages (integer)
   - CopiesAvailable (integer)
   - Price (decimal)

---

### **2. Insert Data**

**Insert the following records into the `Library` table:**

| BookID | Title                | Author        | Publisher      | Genre        | PublishedYear | ISBN           | Pages | CopiesAvailable | Price  |
|--------|----------------------|---------------|----------------|--------------|---------------|----------------|-------|-----------------|--------|
| 1      | To Kill a Mockingbird | Harper Lee    | J.B. Lippincott| Fiction      | 1960          | 978-0061120084 | 324   | 5               | 15.99  |
| 2      | 1984                 | George Orwell | Harvill Secker | Dystopian    | 1949          | 978-0451524935 | 328   | 2               | 9.99   |
| 3      | The Great Gatsby     | F. Scott Fitzgerald | Scribner  | Fiction      | 1925          | 978-0743273565 | 180   | 3               | 10.99  |
| 4      | The Catcher in the Rye | J.D. Salinger | Little, Brown | Fiction      | 1951          | 978-0316769488 | 277   | 4               | 12.99  |
| 5      | The Hobbit           | J.R.R. Tolkien| HarperCollins  | Fantasy      | 1937          | 978-0618968633 | 310   | 6               | 13.99  |

---

### **3. Update Queries with Multiple Conditions**

3. **Update the Price of the book with ISBN '978-0451524935' to 11.99 if the Genre is 'Dystopian' and the PublishedYear is before 1950.**

4. **Update the number of Copies Available to 10 for all books with 'Fiction' genre and a published year after 1950.**

5. **Set the Price of books to 5% less for all books in the 'Fiction' genre with more than 300 pages.**

6. **Update the Pages of books to 350 if the Copies Available are greater than 4 and the Price is below 14.**

7. **Increase the Price by 10% for all books in the 'Fantasy' genre published before 1950 and with less than 300 pages.**

8. **Set the Copies Available to 0 for books where the Price is greater than 12 and the Genre is either 'Fiction' or 'Dystopian'.**

9. **Update the PublishedYear to 2020 for all books with 'Tolkien' in the author’s name, where the price is greater than 10 and less than 15.**

10. **Set the Price to 8.99 for books with 'George Orwell' in the author’s name and having more than 300 pages.**

11. **Decrease the Price of all books in the 'Fiction' genre published before 1950 by 15%, if the Copies Available are less than 5.**

12. **Update the Price of 'To Kill a Mockingbird' to 17.99 if the PublishedYear is 1960 and CopiesAvailable is greater than 4.**

---

### **4. Delete Queries with Multiple Conditions**

13. **Delete books with the ISBN '978-0451524935' and '978-0618968633' if they belong to the 'Dystopian' genre and have more than 2 copies available.**

14. **Delete all books published before 1950 that have a price lower than 10.**

15. **Delete books in the 'Fiction' genre with less than 3 copies available, published before 1960.**

16. **Delete all books with fewer than 200 pages and where the PublishedYear is greater than 1920 but less than 1960.**

17. **Delete books where the author's name is 'Harper Lee' and the price is less than 12.**

18. **Delete all books where Copies Available is 0 and the price is greater than 15.**

19. **Delete all books with ISBN containing '978-074', where the Genre is 'Fiction' and PublishedYear is before 1950.**

20. **Delete all books published after 2000 that have a price below 10 or greater than 15.**

21. **Delete books in the 'Fantasy' genre where the number of Copies Available is greater than 3 but less than 10.**

22. **Delete books with 'J.D. Salinger' as the author, and where the number of pages is less than 300 and the price is greater than 12.**

---

### **5. Select Queries with Multiple Conditions**

23. **Find books in the 'Fiction' genre that were published after 1950, have more than 200 pages, and the price is between 10 and 15.**

24. **List all books with more than 300 pages and a price greater than 12, excluding books published in the 'Fantasy' genre.**

25. **Get a list of books that were published between 1925 and 1950, are priced below 13, and have more than 3 copies available.**

26. **Find books by 'Harper Lee' or 'George Orwell', where the PublishedYear is greater than 1950 and the price is greater than 10.**

27. **List books by 'J.R.R. Tolkien' where Copies Available is greater than 5, and price is between 12 and 15.**

28. **Find the book with the highest price and more than 300 pages published in the 'Dystopian' or 'Fantasy' genre.**

29. **Show all books with 'Tolkien' in the author’s name and PublishedYear before 1940, where Copies Available is between 4 and 6.**

30. **List books in the 'Fiction' genre that have more than 200 pages and a price between 10 and 20, where Copies Available is between 2 and 5.**

31. **Find all books published before 1950, with a price lower than 15, and having fewer than 3 copies available.**

32. **Show titles and authors of books that have a price greater than 12, Copies Available more than 4, and PublishedYear after 1930.**

---
Here are the SQL queries for each of the questions listed:

---

### **1. Create Table Query**
```sql
CREATE TABLE Library (
    BookID INT AUTO_INCREMENT PRIMARY KEY,
    Title VARCHAR(255),
    Author VARCHAR(255),
    Publisher VARCHAR(255),
    Genre VARCHAR(100),
    PublishedYear INT,
    ISBN VARCHAR(20) UNIQUE,
    Pages INT,
    CopiesAvailable INT,
    Price DECIMAL(10, 2)
);
```

---

### **2. Insert Data**

```sql
INSERT INTO Library (Title, Author, Publisher, Genre, PublishedYear, ISBN, Pages, CopiesAvailable, Price)
VALUES 
('To Kill a Mockingbird', 'Harper Lee', 'J.B. Lippincott', 'Fiction', 1960, '978-0061120084', 324, 5, 15.99),
('1984', 'George Orwell', 'Harvill Secker', 'Dystopian', 1949, '978-0451524935', 328, 2, 9.99),
('The Great Gatsby', 'F. Scott Fitzgerald', 'Scribner', 'Fiction', 1925, '978-0743273565', 180, 3, 10.99),
('The Catcher in the Rye', 'J.D. Salinger', 'Little, Brown', 'Fiction', 1951, '978-0316769488', 277, 4, 12.99),
('The Hobbit', 'J.R.R. Tolkien', 'HarperCollins', 'Fantasy', 1937, '978-0618968633', 310, 6, 13.99);
```

---

### **3. Update Queries with Multiple Conditions**

1. **Update Price for ISBN '978-0451524935' with Genre 'Dystopian' and PublishedYear before 1950:**
```sql
UPDATE Library 
SET Price = 11.99 
WHERE ISBN = '978-0451524935' 
  AND Genre = 'Dystopian' 
  AND PublishedYear < 1950;
```

2. **Update Copies Available for books in the 'Fiction' genre, PublishedYear after 1950:**
```sql
UPDATE Library 
SET CopiesAvailable = 10 
WHERE Genre = 'Fiction' 
  AND PublishedYear > 1950;
```

3. **Set the Price 5% less for books in 'Fiction' genre with more than 300 pages:**
```sql
UPDATE Library 
SET Price = Price * 0.95 
WHERE Genre = 'Fiction' 
  AND Pages > 300;
```

4. **Update Pages to 350 for books with more than 4 Copies Available and Price below 14:**
```sql
UPDATE Library 
SET Pages = 350 
WHERE CopiesAvailable > 4 
  AND Price < 14;
```

5. **Increase Price by 10% for books in 'Fantasy' genre published before 1950 and with less than 300 pages:**
```sql
UPDATE Library 
SET Price = Price * 1.10 
WHERE Genre = 'Fantasy' 
  AND PublishedYear < 1950 
  AND Pages < 300;
```

6. **Set Copies Available to 0 for books where Price is greater than 12 and Genre is 'Fiction' or 'Dystopian':**
```sql
UPDATE Library 
SET CopiesAvailable = 0 
WHERE Price > 12 
  AND Genre IN ('Fiction', 'Dystopian');
```

7. **Update PublishedYear to 2020 for books by 'Tolkien', with Price between 10 and 15:**
```sql
UPDATE Library 
SET PublishedYear = 2020 
WHERE Author LIKE '%Tolkien%' 
  AND Price BETWEEN 10 AND 15;
```

8. **Set Price to 8.99 for books with 'George Orwell' in the author’s name and more than 300 pages:**
```sql
UPDATE Library 
SET Price = 8.99 
WHERE Author LIKE 'George Orwell' 
  AND Pages > 300;
```

9. **Decrease Price by 15% for books in 'Fiction' genre published before 1950 and Copies Available less than 5:**
```sql
UPDATE Library 
SET Price = Price * 0.85 
WHERE Genre = 'Fiction' 
  AND PublishedYear < 1950 
  AND CopiesAvailable < 5;
```

10. **Update Price of 'To Kill a Mockingbird' to 17.99 if PublishedYear is 1960 and CopiesAvailable > 4:**
```sql
UPDATE Library 
SET Price = 17.99 
WHERE Title = 'To Kill a Mockingbird' 
  AND PublishedYear = 1960 
  AND CopiesAvailable > 4;
```

---

### **4. Delete Queries with Multiple Conditions**

1. **Delete books with ISBN '978-0451524935' and '978-0618968633', where Genre is 'Dystopian' and Copies Available > 2:**
```sql
DELETE FROM Library 
WHERE ISBN IN ('978-0451524935', '978-0618968633') 
  AND Genre = 'Dystopian' 
  AND CopiesAvailable > 2;
```

2. **Delete books published before 1950 with a price lower than 10:**
```sql
DELETE FROM Library 
WHERE PublishedYear < 1950 
  AND Price < 10;
```

3. **Delete books in 'Fiction' genre with less than 3 copies available and published before 1960:**
```sql
DELETE FROM Library 
WHERE Genre = 'Fiction' 
  AND CopiesAvailable < 3 
  AND PublishedYear < 1960;
```

4. **Delete books with fewer than 200 pages, PublishedYear > 1920 and < 1960:**
```sql
DELETE FROM Library 
WHERE Pages < 200 
  AND PublishedYear > 1920 
  AND PublishedYear < 1960;
```

5. **Delete books where Author is 'Harper Lee' and Price is less than 12:**
```sql
DELETE FROM Library 
WHERE Author = 'Harper Lee' 
  AND Price < 12;
```

6. **Delete books with Copies Available = 0 and Price > 15:**
```sql
DELETE FROM Library 
WHERE CopiesAvailable = 0 
  AND Price > 15;
```

7. **Delete books with ISBN '978-0743273565' where Genre is 'Fiction' and PublishedYear < 1950:**
```sql
DELETE FROM Library 
WHERE ISBN = '978-0743273565' 
  AND Genre = 'Fiction' 
  AND PublishedYear < 1950;
```

8. **Delete books published after 2000 with Price between 10 and 15 or greater than 15:**
```sql
DELETE FROM Library 
WHERE PublishedYear > 2000 
  AND (Price BETWEEN 10 AND 15 OR Price > 15);
```

9. **Delete books in 'Fantasy' genre with Copies Available > 3 but < 10:**
```sql
DELETE FROM Library 
WHERE Genre = 'Fantasy' 
  AND CopiesAvailable > 3 
  AND CopiesAvailable < 10;
```

10. **Delete books by 'J.D. Salinger' where Pages < 300 and Price > 12:**
```sql
DELETE FROM Library 
WHERE Author = 'J.D. Salinger' 
  AND Pages < 300 
  AND Price > 12;
```

---

### **5. Select Queries with Multiple Conditions**

1. **Find books in 'Fiction' genre, PublishedYear after 1950, more than 200 pages, and Price between 10 and 15:**
```sql
SELECT * 
FROM Library 
WHERE Genre = 'Fiction' 
  AND PublishedYear > 1950 
  AND Pages > 200 
  AND Price BETWEEN 10 AND 15;
```

2. **List books with more than 300 pages, Price > 12, excluding 'Fantasy' genre:**
```sql
SELECT * 
FROM Library 
WHERE Pages > 300 
  AND Price > 12 
  AND Genre != 'Fantasy';
```

3. **Get books published between 1925 and 1950, Price < 13, and Copies Available > 3:**
```sql
SELECT * 
FROM Library 
WHERE PublishedYear BETWEEN 1925 AND 1950 
  AND Price < 13 
  AND CopiesAvailable > 3;
```

4. **Find books by 'Harper Lee' or 'George Orwell' where PublishedYear > 1950 and Price > 10:**
```sql
SELECT * 
FROM Library 
WHERE (Author = 'Harper Lee' OR Author = 'George Orwell') 
  AND PublishedYear > 1950 
  AND Price > 10;
```

5. **List books by 'J.R.R. Tolkien' with Copies Available > 5, and Price between 12 and 15:**
```sql
SELECT * 
FROM Library 
WHERE Author = 'J.R.R. Tolkien' 
  AND CopiesAvailable > 5 
  AND Price BETWEEN 12 AND 15;
```

6. **Find the book with the highest price, more than 300 pages, in 'Dystopian' or 'Fantasy' genre:**
```sql
SELECT * 
FROM Library 
WHERE (Genre = 'Dystopian' OR Genre = 'Fantasy') 
  AND Pages > 300 
ORDER BY Price DESC 
LIMIT 1;
```

7. **Show all books with 'Tolkien' in the author’s name, PublishedYear before 1940, Copies Available between 4 and 6:**
```sql
SELECT * 
FROM Library 
WHERE Author LIKE '%Tolkien%' 
  AND PublishedYear < 1940 
  AND CopiesAvailable BETWEEN 4 AND 6;
```

8. **List books in 'Fiction' genre with more than 200 pages and Price between 10 and 20, Copies Available between 2 and 5:**
```sql
SELECT * 
FROM Library 
WHERE Genre = 'Fiction' 
  AND Pages > 200 
  AND Price BETWEEN 10 AND 20 
  AND CopiesAvailable BETWEEN 2 AND 5;
```

9. **Find all books published before 1950, Price < 15, and Copies Available < 3:**
```sql
SELECT * 
FROM Library 
WHERE PublishedYear < 1950 
  AND Price < 15 
  AND CopiesAvailable < 3;
```

10. **Show titles and authors of books with Price > 12, Copies Available > 4, PublishedYear > 1930:**
```sql
SELECT Title, Author 
FROM Library 
WHERE Price > 12 
  AND CopiesAvailable > 4 
  AND PublishedYear > 1930;
```

---

These queries cover a variety of complex conditions, making it ideal for practicing CRUD operations with multiple conditions.