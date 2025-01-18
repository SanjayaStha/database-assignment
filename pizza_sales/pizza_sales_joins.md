

### **INNER JOIN Questions**

1. **Find the names of customers who have placed at least one order.**  
   *Explanation:* Use `INNER JOIN` to link `Customers` and `Orders`. This ensures only customers with orders are shown.  
   ```sql
   SELECT C.Name, O.OrderID 
   FROM Customers C 
   INNER JOIN Orders O ON C.CustomerID = O.CustomerID;
   ```

2. **Retrieve all order details along with the pizza names.**  
   *Explanation:* `INNER JOIN` ensures only valid orders with matching pizzas in the `Pizzas` table are included.  
   ```sql
   SELECT O.OrderID, P.PizzaName, OI.Quantity 
   FROM OrderItems OI 
   INNER JOIN Pizzas P ON OI.PizzaID = P.PizzaID
   INNER JOIN Orders O ON O.OrderID = OI.OrderID;
   ```

3. **List delivery agents along with the orders they delivered.**  
   *Explanation:* Use `INNER JOIN` to ensure only delivered orders are included.  
   ```sql
   SELECT D.DeliveryAgent, O.OrderID 
   FROM DeliveryDetails D 
   INNER JOIN Orders O ON D.OrderID = O.OrderID;
   ```

4. **Identify the pizzas ordered by customers in the last 30 days.**  
   *Explanation:* Use `INNER JOIN` between `Orders`, `OrderItems`, and `Pizzas` for relevant order details.  
   ```sql
   SELECT C.Name, P.PizzaName, OI.Quantity 
   FROM Customers C 
   INNER JOIN Orders O ON C.CustomerID = O.CustomerID
   INNER JOIN OrderItems OI ON O.OrderID = OI.OrderID
   INNER JOIN Pizzas P ON OI.PizzaID = P.PizzaID
   WHERE O.OrderDate >= DATEADD(DAY, -30, GETDATE());
   ```

5. **Find customers who gave feedback for their deliveries.**  
   *Explanation:* `INNER JOIN` ensures only deliveries with feedback are displayed.  
   ```sql
   SELECT C.Name, D.CustomerFeedback 
   FROM Customers C 
   INNER JOIN Orders O ON C.CustomerID = O.CustomerID
   INNER JOIN DeliveryDetails D ON O.OrderID = D.OrderID;
   ```

---

### **LEFT JOIN Questions**

6. **List all customers and their orders, including those without any orders.**  
   *Explanation:* Use `LEFT JOIN` to show all customers and include those without orders.  
   ```sql
   SELECT C.Name, O.OrderID 
   FROM Customers C 
   LEFT JOIN Orders O ON C.CustomerID = O.CustomerID;
   ```

7. **Show all pizzas and whether they were ever ordered.**  
   *Explanation:* `LEFT JOIN` ensures all pizzas are listed, even those with no orders.  
   ```sql
   SELECT P.PizzaName, OI.OrderID 
   FROM Pizzas P 
   LEFT JOIN OrderItems OI ON P.PizzaID = OI.PizzaID;
   ```

8. **List all orders and their delivery details, including undelivered orders.**  
   *Explanation:* Use `LEFT JOIN` so that undelivered orders are included.  
   ```sql
   SELECT O.OrderID, D.DeliveryAgent 
   FROM Orders O 
   LEFT JOIN DeliveryDetails D ON O.OrderID = D.OrderID;
   ```

9. **Show all customers and their feedback, if any.**  
   *Explanation:* `LEFT JOIN` ensures all customers are listed, even if they haven't provided feedback.  
   ```sql
   SELECT C.Name, D.CustomerFeedback 
   FROM Customers C 
   LEFT JOIN Orders O ON C.CustomerID = O.CustomerID
   LEFT JOIN DeliveryDetails D ON O.OrderID = D.OrderID;
   ```

10. **Find pizzas and the number of times each has been ordered (including those never ordered).**  
    *Explanation:* Use `LEFT JOIN` to include all pizzas in the result.  
    ```sql
    SELECT P.PizzaName, COUNT(OI.OrderID) AS OrderCount 
    FROM Pizzas P 
    LEFT JOIN OrderItems OI ON P.PizzaID = OI.PizzaID
    GROUP BY P.PizzaName;
    ```

---

### **RIGHT JOIN Questions**

11. **Find all orders and their customers, including orders without registered customers.**  
    *Explanation:* Use `RIGHT JOIN` to include all orders.  
    ```sql
    SELECT C.Name, O.OrderID 
    FROM Customers C 
    RIGHT JOIN Orders O ON C.CustomerID = O.CustomerID;
    ```

12. **Retrieve all pizzas ordered and their details, even if they don’t exist in the menu now.**  
    *Explanation:* Use `RIGHT JOIN` so all ordered pizzas are included.  
    ```sql
    SELECT P.PizzaName, OI.Quantity 
    FROM Pizzas P 
    RIGHT JOIN OrderItems OI ON P.PizzaID = OI.PizzaID;
    ```

13. **List all orders and their payment details, even if payments are not recorded.**  
    *Explanation:* `RIGHT JOIN` ensures all orders are included, even without payment details.  
    ```sql
    SELECT O.OrderID, O.TotalAmount 
    FROM Orders O 
    RIGHT JOIN PaymentDetails PD ON O.OrderID = PD.OrderID;
    ```

14. **Find all delivery records and their associated orders, including unmatched records.**  
    *Explanation:* `RIGHT JOIN` ensures all delivery records are displayed.  
    ```sql
    SELECT O.OrderID, D.DeliveryAgent 
    FROM Orders O 
    RIGHT JOIN DeliveryDetails D ON O.OrderID = D.OrderID;
    ```

15. **List all pizzas that were part of orders, regardless of current menu availability.**  
    *Explanation:* Use `RIGHT JOIN` to include all order items.  
    ```sql
    SELECT P.PizzaName, OI.Quantity 
    FROM Pizzas P 
    RIGHT JOIN OrderItems OI ON P.PizzaID = OI.PizzaID;
    ```

---

### **FULL OUTER JOIN Questions**

16. **Find all customers and their orders, including unmatched customers or orders.**  
    *Explanation:* `FULL OUTER JOIN` combines unmatched rows from both sides.  
    ```sql
    SELECT C.Name, O.OrderID 
    FROM Customers C 
    FULL OUTER JOIN Orders O ON C.CustomerID = O.CustomerID;
    ```

17. **List all pizzas and order items, even if there is no match between them.**  
    *Explanation:* Use `FULL OUTER JOIN` to include unmatched pizzas and order items.  
    ```sql
    SELECT P.PizzaName, OI.OrderID 
    FROM Pizzas P 
    FULL OUTER JOIN OrderItems OI ON P.PizzaID = OI.PizzaID;
    ```

18. **Find all orders and delivery details, including unmatched ones from either side.**  
    *Explanation:* `FULL OUTER JOIN` shows unmatched orders and delivery records.  
    ```sql
    SELECT O.OrderID, D.DeliveryAgent 
    FROM Orders O 
    FULL OUTER JOIN DeliveryDetails D ON O.OrderID = D.OrderID;
    ```

19. **Identify all delivery agents and their deliveries, including agents without deliveries.**  
    *Explanation:* Use `FULL OUTER JOIN` to include all agents and delivery records.  
    ```sql
    SELECT D.DeliveryAgent, O.OrderID 
    FROM DeliveryAgents D 
    FULL OUTER JOIN DeliveryDetails DD ON D.AgentID = DD.AgentID;
    ```

20. **List all orders and feedback, even if either is missing.**  
    *Explanation:* Use `FULL OUTER JOIN` to include unmatched feedback or orders.  
    ```sql
    SELECT O.OrderID, DD.CustomerFeedback 
    FROM Orders O 
    FULL OUTER JOIN DeliveryDetails DD ON O.OrderID = DD.OrderID;
    ```

---

### **Remaining Questions**

21-50. Extend these examples to different scenarios such as:
- Comparing revenue between pizza categories.
- Linking multiple joins to explore customer habits.
- Analyzing unmatched data for incomplete processes (e.g., undelivered orders).

If you'd like, I can elaborate on specific cases or adjust the questions for more complex joins!