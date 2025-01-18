Here's a detailed scenario for managing a pizza sales database with tables and queries to practice SQL:

---

### **Scenario: Pizza Sales Database**

**Business Context:**
- A pizza restaurant sells various types of pizzas, categorized as Veg and Non-Veg.
- Customers place orders online or in-store, and orders can include multiple pizzas with additional toppings.
- Delivery is handled by delivery agents.
- Sales data has been collected for the past 5 years.

**Requirements:**
1. Track pizza details: names, categories, sizes, prices, and ingredients.
2. Maintain customer information: names, contact details, and addresses.
3. Store order details: order date, total amount, payment method, and delivery status.
4. Record order items: specific pizzas ordered, size, quantity, and additional toppings.
5. Track delivery details: assigned delivery agent, delivery time, and customer feedback.

---

### **Database Tables**

1. **Pizzas**
   - `PizzaID` (Primary Key)
   - `PizzaName`
   - `Category` (Veg/Non-Veg)
   - `Size` (Small, Medium, Large)
   - `Price`
   - `Ingredients`

2. **Customers**
   - `CustomerID` (Primary Key)
   - `Name`
   - `PhoneNumber`
   - `Email`
   - `Address`

3. **Orders**
   - `OrderID` (Primary Key)
   - `CustomerID` (Foreign Key)
   - `OrderDate`
   - `TotalAmount`
   - `PaymentMethod` (Cash, Card, Online)
   - `DeliveryStatus` (Delivered, Canceled, Pending)

4. **OrderItems**
   - `OrderItemID` (Primary Key)
   - `OrderID` (Foreign Key)
   - `PizzaID` (Foreign Key)
   - `Size`
   - `Quantity`
   - `AdditionalToppings`

5. **DeliveryDetails**
   - `DeliveryID` (Primary Key)
   - `OrderID` (Foreign Key)
   - `DeliveryAgent`
   - `DeliveryTime`
   - `CustomerFeedback`

6. **SalesAnalytics**
   - `Date` (Primary Key)
   - `TotalOrders`
   - `TotalRevenue`
   - `MostSoldPizza`

---

### **Query List**

#### **Basic Queries**
1. Retrieve all Veg pizzas with their sizes and prices.
2. Find the details of a specific customer using their phone number.
3. List all orders placed in the last 7 days.
4. Show the total amount of a specific order using its OrderID.
5. Retrieve the names of delivery agents and the number of orders they delivered.

#### **Intermediate Queries**
6. Find the most popular pizza in the last month.
7. Calculate the total revenue generated in a specific year.
8. Show all orders with more than three pizzas.
9. Identify customers who have placed more than 5 orders.
10. Retrieve the details of the largest order by total amount.

#### **Analytical Queries**
11. Determine the average order value for each year.
12. List the top 5 customers based on the total amount spent.
13. Find the month with the highest sales in the last 5 years.
14. Compare the revenue from Veg and Non-Veg pizzas.
15. Identify the most frequent additional topping ordered.

#### **Date and Time Queries**
16. Retrieve orders placed between 6 PM and 9 PM.
17. Find the delivery time of orders completed on a specific date.
18. Identify days with zero revenue in the past year.
19. List all orders that were delivered late (assuming a 30-minute delivery standard).
20. Calculate the average delivery time for each delivery agent.

#### **Join Queries**
21. List the details of pizzas ordered in a specific order.
22. Retrieve all customer details along with their last order.
23. Show the pizzas ordered by a specific customer along with the delivery status.
24. Identify orders along with customer feedback for those with negative ratings.
25. Find the pizza ingredients for each order item.

#### **Grouping and Aggregation**
26. Count the total number of orders for each customer.
27. Calculate the monthly revenue for each year.
28. Determine the top 3 pizzas sold for each category (Veg/Non-Veg).
29. Identify the delivery agent with the highest average rating.
30. Count the number of orders paid by each payment method.

#### **Subqueries**
31. Find customers who have never ordered a Non-Veg pizza.
32. Identify orders with a total amount above the average order value.
33. Retrieve the names of pizzas that have never been ordered.
34. Find the most expensive pizza ordered by any customer.
35. List all orders placed by the top customer (based on total spending).

#### **Advanced Queries**
36. Analyze the sales trend over the last 5 years (year-over-year growth).
37. Predict the most sold pizza next month based on historical data.
38. Determine the correlation between order quantity and total revenue.
39. Identify customer clusters based on their order history.
40. Find patterns in late deliveries.

#### **Data Modification Queries**
41. Add a new pizza to the menu.
42. Update the price of a specific pizza.
43. Delete an order that was canceled.
44. Change the delivery agent for a specific order.
45. Add customer feedback for a delivered order.

#### **Performance and Optimization**
46. Create an index to speed up queries on `OrderDate`.
47. Analyze the effect of indexing `CustomerID` on query performance.
48. Partition the `Orders` table by year and calculate the total revenue for each partition.
49. Optimize a query to find the top 3 pizzas sold in the last year.
50. Create a view to summarize daily revenue and most sold pizzas.

---

This setup provides comprehensive coverage for SQL practice, including CRUD operations, analytical functions, performance optimization, and real-life business scenarios.