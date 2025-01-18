

1. **Retrieve all Veg pizzas with their sizes and prices:**
   ```sql
   SELECT PizzaName, Size, Price 
   FROM Pizzas 
   WHERE Category = 'Veg';
   ```

2. **Find the details of a specific customer using their phone number:**
   ```sql
   SELECT * 
   FROM Customers 
   WHERE PhoneNumber = '1234567890';
   ```

3. **List all orders placed in the last 7 days:**
   ```sql
   SELECT * 
   FROM Orders 
   WHERE OrderDate >= DATEADD(DAY, -7, GETDATE());
   ```

4. **Show the total amount of a specific order using its OrderID:**
   ```sql
   SELECT TotalAmount 
   FROM Orders 
   WHERE OrderID = 101;
   ```

5. **Retrieve the names of delivery agents and the number of orders they delivered:**
   ```sql
   SELECT DeliveryAgent, COUNT(*) AS OrderCount 
   FROM DeliveryDetails 
   GROUP BY DeliveryAgent;
   ```

---

### **Intermediate Queries**

6. **Find the most popular pizza in the last month:**
   ```sql
   SELECT PizzaID, COUNT(*) AS TotalOrdered 
   FROM OrderItems 
   WHERE OrderID IN (
       SELECT OrderID 
       FROM Orders 
       WHERE OrderDate >= DATEADD(MONTH, -1, GETDATE())
   )
   GROUP BY PizzaID 
   ORDER BY TotalOrdered DESC 
   LIMIT 1;
   ```

7. **Calculate the total revenue generated in a specific year:**
   ```sql
   SELECT SUM(TotalAmount) AS TotalRevenue 
   FROM Orders 
   WHERE YEAR(OrderDate) = 2024;
   ```

8. **Show all orders with more than three pizzas:**
   ```sql
   SELECT OrderID 
   FROM OrderItems 
   GROUP BY OrderID 
   HAVING SUM(Quantity) > 3;
   ```

9. **Identify customers who have placed more than 5 orders:**
   ```sql
   SELECT CustomerID, COUNT(*) AS OrderCount 
   FROM Orders 
   GROUP BY CustomerID 
   HAVING OrderCount > 5;
   ```

10. **Retrieve the details of the largest order by total amount:**
    ```sql
    SELECT * 
    FROM Orders 
    ORDER BY TotalAmount DESC 
    LIMIT 1;
    ```

---

### **Analytical Queries**

11. **Determine the average order value for each year:**
    ```sql
    SELECT YEAR(OrderDate) AS Year, AVG(TotalAmount) AS AvgOrderValue 
    FROM Orders 
    GROUP BY YEAR(OrderDate);
    ```

12. **List the top 5 customers based on the total amount spent:**
    ```sql
    SELECT CustomerID, SUM(TotalAmount) AS TotalSpent 
    FROM Orders 
    GROUP BY CustomerID 
    ORDER BY TotalSpent DESC 
    LIMIT 5;
    ```

13. **Find the month with the highest sales in the last 5 years:**
    ```sql
    SELECT YEAR(OrderDate) AS Year, MONTH(OrderDate) AS Month, SUM(TotalAmount) AS MonthlySales 
    FROM Orders 
    WHERE OrderDate >= DATEADD(YEAR, -5, GETDATE())
    GROUP BY YEAR(OrderDate), MONTH(OrderDate) 
    ORDER BY MonthlySales DESC 
    LIMIT 1;
    ```

14. **Compare the revenue from Veg and Non-Veg pizzas:**
    ```sql
    SELECT P.Category, SUM(OI.Quantity * P.Price) AS TotalRevenue 
    FROM OrderItems OI
    JOIN Pizzas P ON OI.PizzaID = P.PizzaID
    GROUP BY P.Category;
    ```

15. **Identify the most frequent additional topping ordered:**
    ```sql
    SELECT AdditionalToppings, COUNT(*) AS Frequency 
    FROM OrderItems 
    WHERE AdditionalToppings IS NOT NULL
    GROUP BY AdditionalToppings 
    ORDER BY Frequency DESC 
    LIMIT 1;
    ```

---

### **Join Queries**

16. **List the details of pizzas ordered in a specific order:**
    ```sql
    SELECT OI.OrderItemID, P.PizzaName, OI.Size, OI.Quantity 
    FROM OrderItems OI
    JOIN Pizzas P ON OI.PizzaID = P.PizzaID 
    WHERE OI.OrderID = 101;
    ```

17. **Retrieve all customer details along with their last order:**
    ```sql
    SELECT C.*, O.OrderID, O.OrderDate 
    FROM Customers C
    JOIN Orders O ON C.CustomerID = O.CustomerID
    WHERE O.OrderDate = (
        SELECT MAX(OrderDate) 
        FROM Orders 
        WHERE CustomerID = C.CustomerID
    );
    ```

---

The rest of the queries follow similar logic, depending on specific requirements. 

Would you like me to create a mock dataset or generate further detailed answers for any particular set of questions?