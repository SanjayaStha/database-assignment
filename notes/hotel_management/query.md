
---

## **i. Customers Who Have Not Made Any Reservation Since 2023**
```sql
SELECT c.FirstName, c.LastName, c.Email, c.ContactNumber
FROM Customer c
LEFT JOIN Reservation r ON c.CustomerID = r.CustomerID AND r.BookingDate >= '2023-01-01'
WHERE r.ReservationID IS NULL;
```
### ✅ **Explanation:**
- Retrieves customers **who have never made a reservation** since **January 1, 2023**.
- Uses **LEFT JOIN** to include all customers and **filters out those who have reservations** using `WHERE r.ReservationID IS NULL`.

---

## **ii. Monthly Revenue for 2023 (Descending Order)**
```sql
SELECT 
    FORMAT(PaymentDate, 'yyyy-MM') AS Month,
    SUM(TotalAmount) AS MonthlyRevenue
FROM Invoice
WHERE PaymentDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY FORMAT(PaymentDate, 'yyyy-MM')
ORDER BY MonthlyRevenue DESC;
```
### ✅ **Explanation:**
- Groups total revenue (`SUM(TotalAmount)`) by **month**.
- Uses `FORMAT(PaymentDate, 'yyyy-MM')` to extract the year and month.
- Orders the results **in descending order** by revenue.

---

## **iii. Customers Who Made More Than 3 Reservations in 2023**
```sql
SELECT c.CustomerID, c.FirstName, c.LastName, COUNT(r.ReservationID) AS ReservationCount
FROM Customer c
JOIN Reservation r ON c.CustomerID = r.CustomerID
WHERE r.BookingDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY c.CustomerID, c.FirstName, c.LastName
HAVING COUNT(r.ReservationID) > 3;
```
### ✅ **Explanation:**
- Counts the number of reservations **per customer**.
- Filters only those who made **more than 3 reservations** in 2023.

---

## **iv. Average Rating & Total Reviews Per Room Type (Kuala Lumpur Branch)**
```sql
SELECT r.RoomType, 
       AVG(rv.Rating) AS AvgRating, 
       COUNT(rv.ReviewID) AS TotalReviews
FROM Review rv
JOIN Reservation res ON rv.CustomerID = res.CustomerID
JOIN Room r ON res.BranchID = r.BranchID
JOIN Branch b ON r.BranchID = b.BranchID
WHERE b.BranchName = 'Kuala Lumpur'
GROUP BY r.RoomType;
```
### ✅ **Explanation:**
- Joins **Review**, **Reservation**, **Room**, and **Branch** tables.
- Filters only **Kuala Lumpur branch** and calculates:
  - **Average rating** (`AVG(Rating)`)
  - **Total reviews** (`COUNT(ReviewID)`) for each **room type**.

---

## **v. Total Revenue by Each Branch (2023)**
```sql
SELECT b.BranchID, b.BranchName, SUM(i.TotalAmount) AS TotalRevenue
FROM Invoice i
JOIN Reservation r ON i.ReservationID = r.ReservationID
JOIN Branch b ON r.BranchID = b.BranchID
WHERE i.PaymentDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY b.BranchID, b.BranchName;
```
### ✅ **Explanation:**
- Groups total **revenue per branch**.
- Joins **Invoice**, **Reservation**, and **Branch** tables.

---

## **vi. Customers & Total Amount Spent in 2023**
```sql
SELECT c.CustomerID, c.FirstName, c.LastName, SUM(i.TotalAmount) AS TotalSpent
FROM Customer c
JOIN Reservation r ON c.CustomerID = r.CustomerID
JOIN Invoice i ON r.ReservationID = i.ReservationID
WHERE i.PaymentDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY c.CustomerID, c.FirstName, c.LastName;
```
### ✅ **Explanation:**
- Retrieves **total spending per customer** in 2023.

---

## **vii. Average & Total Spending by Gender (2023)**
```sql
SELECT c.Gender, 
       AVG(i.TotalAmount) AS AvgSpent, 
       SUM(i.TotalAmount) AS TotalSpent
FROM Customer c
JOIN Reservation r ON c.CustomerID = r.CustomerID
JOIN Invoice i ON r.ReservationID = i.ReservationID
WHERE i.PaymentDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY c.Gender;
```
### ✅ **Explanation:**
- Groups by **Gender** (assumes `Customer` table has a `Gender` column).
- Calculates:
  - **Average spending** (`AVG(TotalAmount)`)
  - **Total spending** (`SUM(TotalAmount)`)

---

## **viii. Branch Details with Total Rooms**
```sql
SELECT b.BranchID, b.Location, CONCAT(m.FirstName, ' ', m.LastName) AS ManagerName, 
       COUNT(r.RoomID) AS TotalRooms
FROM Branch b
LEFT JOIN Manager m ON b.BranchID = m.BranchID
LEFT JOIN Room r ON b.BranchID = r.BranchID
GROUP BY b.BranchID, b.Location, m.FirstName, m.LastName;
```
### ✅ **Explanation:**
- Displays **Branch ID, Address, Manager’s Name, Total Rooms**.
- Uses `LEFT JOIN` to **include branches without a manager or rooms**.

---

## **ix. Customer with Highest Reservations & Their Average Spending**
```sql
WITH ReservationCount AS (
    SELECT c.CustomerID, c.FirstName, c.LastName, COUNT(r.ReservationID) AS TotalReservations
    FROM Customer c
    JOIN Reservation r ON c.CustomerID = r.CustomerID
    WHERE r.BookingDate BETWEEN '2023-01-01' AND '2023-12-31'
    GROUP BY c.CustomerID, c.FirstName, c.LastName
)
SELECT rc.CustomerID, rc.FirstName, rc.LastName, rc.TotalReservations, 
       AVG(i.TotalAmount) AS AvgSpent
FROM ReservationCount rc
JOIN Reservation r ON rc.CustomerID = r.CustomerID
JOIN Invoice i ON r.ReservationID = i.ReservationID
WHERE rc.TotalReservations = (SELECT MAX(TotalReservations) FROM ReservationCount)
GROUP BY rc.CustomerID, rc.FirstName, rc.LastName, rc.TotalReservations;
```
### ✅ **Explanation:**
- Finds the **customer with the most reservations**.
- Uses **Common Table Expression (CTE)** to count reservations first.
- Then, retrieves **their average amount spent**.

---

## **x. Customers Who Stayed in More Than One Branch (2023)**
```sql
SELECT c.CustomerID, c.FirstName, c.LastName, COUNT(DISTINCT r.BranchID) AS TotalBranches
FROM Customer c
JOIN Reservation r ON c.CustomerID = r.CustomerID
WHERE r.BookingDate BETWEEN '2023-01-01' AND '2023-12-31'
GROUP BY c.CustomerID, c.FirstName, c.LastName
HAVING COUNT(DISTINCT r.BranchID) > 1;
```
### ✅ **Explanation:**
- **Counts distinct branches** where each customer stayed.
- Filters **only customers who stayed in more than one branch** in 2023.

---