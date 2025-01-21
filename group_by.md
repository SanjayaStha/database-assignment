
### Sample Table: **Employee_Salaries**

| Employee_ID | Department | Salary | Bonus | Hire_Date  | Gender | Age | City        | Experience (Years) | Job_Title        | Performance_Rating | Attendance (Days) | Overtime_Hours |
|-------------|------------|--------|-------|------------|--------|-----|-------------|---------------------|------------------|-------------------|-------------------|----------------|
| 1           | HR         | 50000  | 5000  | 2019-01-15 | M      | 28  | New York    | 5                   | HR Manager       | 4                 | 20                | 10             |
| 2           | IT         | 80000  | 8000  | 2020-06-20 | F      | 32  | Chicago     | 4                   | Software Engineer| 5                 | 18                | 15             |
| 3           | HR         | 45000  | 4000  | 2021-09-01 | M      | 25  | New York    | 3                   | HR Assistant     | 3                 | 22                | 8              |
| 4           | Sales      | 60000  | 6000  | 2018-03-10 | F      | 29  | Los Angeles | 6                   | Sales Executive  | 4                 | 19                | 12             |
| 5           | IT         | 75000  | 7000  | 2017-07-30 | M      | 35  | Chicago     | 7                   | Software Engineer| 5                 | 20                | 13             |
| 6           | Sales      | 55000  | 5500  | 2022-05-15 | F      | 27  | Los Angeles | 2                   | Sales Executive  | 4                 | 24                | 9              |
| 7           | Marketing  | 65000  | 6000  | 2020-08-22 | M      | 30  | New York    | 4                   | Marketing Manager| 5                 | 21                | 10             |
| 8           | IT         | 78000  | 7000  | 2019-11-11 | F      | 31  | Chicago     | 5                   | Software Engineer| 4                 | 16                | 20             |
| 9           | Marketing  | 70000  | 6500  | 2018-02-25 | M      | 33  | Los Angeles | 6                   | Marketing Manager| 4                 | 18                | 14             |
| 10          | HR         | 45000  | 4000  | 2021-03-10 | F      | 26  | New York    | 3                   | HR Assistant     | 3                 | 20                | 6              |
| 11          | Sales      | 65000  | 6500  | 2019-05-18 | M      | 34  | Los Angeles | 5                   | Sales Executive  | 5                 | 22                | 11             |
| 12          | IT         | 70000  | 7000  | 2018-09-15 | M      | 30  | Chicago     | 6                   | Software Engineer| 4                 | 18                | 17             |


#### Questions:

1. **Basic `GROUP BY`**: 
   - What is the total salary for each department?
   - How many employees are there in each department?
   - What is the average salary in each department?
   
2. **Using `COUNT`**:
   - How many employees are in each city?
   - What is the count of employees in each job title?
   - How many employees have a performance rating of 4?
   - How many employees in the 'Sales' department have more than 20 days of attendance?

3. **Using `SUM`**:
   - What is the total bonus amount for each department?
   - What is the total salary paid for employees in each city?
   - What is the total overtime hours worked by employees in each department?

4. **Using `AVG`**:
   - What is the average bonus amount for employees in each department?
   - What is the average salary of employees for each job title?
   - What is the average experience (in years) for employees in each city?

5. **Using `MIN` and `MAX`**:
   - What is the minimum salary in each department?
   - What is the maximum salary in each city?
   - What is the highest performance rating by job title?

6. **Using `GROUP BY` with `HAVING`**:
   - Which departments have an average salary greater than 70,000?
   - Which city has an average attendance of more than 20 days per employee?
   - Which job title has more than 5 employees with a performance rating of 4 or higher?

7. **Using `DISTINCT`**:
   - How many distinct cities do employees work in?
   - How many distinct job titles are there in the company?

8. **Using multiple aggregate functions**:
   - What is the average salary and total bonus for each department?
   - What is the total salary and total overtime worked by employees in each city?
   - What is the average performance rating and minimum attendance for employees in each department?

9. **Combining `GROUP BY` with date/time functions**:
   - What is the average salary of employees hired in each year?
   - How many employees joined in each month of the year?
   - What is the average experience of employees hired in 2019?

10. **Grouping by multiple columns**:
    - What is the average salary for each combination of department and job title?
    - What is the total salary for each combination of city and gender?
    - What is the average attendance by department and gender?

11. **Advanced `HAVING` conditions**:
    - Which departments have an average salary greater than 60,000 and fewer than 5 employees?
    - Which departments have more than 3 employees with a performance rating greater than 3?
    
12. **Nested aggregation**:
    - What is the department with the highest average salary from employees with more than 3 years of experience?
    - What is the city with the lowest total salary, considering only employees with over 4 years of experience?

13. **`GROUP BY` with `ORDER BY`**:
    - List the departments with total salary amounts in descending order.
    - List the cities with the most employees in ascending order.

14. **Complex Aggregate Questions**:
    - What is the total salary, average salary, and the count of employees for each job title?
    - Which departments have the highest average bonus, and what is the average bonus amount?

15. **Finding outliers**:
    - Which employee has the highest salary in each department?
    - What is the highest performance rating in each city?

16. **Using `GROUP BY` with specific conditions**:
    - Find the total salary and total overtime hours worked by employees who have more than 10 overtime hours.
    - Find the average age and average salary for employees who have attended more than 20 days.

17. **Complex aggregation with `JOIN`**:
    - If there is another table `Employee_Projects`, how would you find the average salary for employees in each project group?

18. **Using `GROUP BY` for comparisons**:
    - Compare the total salary between male and female employees.
    - Compare the average salary in the 'Sales' and 'Marketing' departments.

19. **Working with data ranges**:
    - Find the departments where the average salary is between 60,000 and 80,000.
    - Which cities have a total salary payout between 400,000 and 500,000?

20. **Dealing with NULL values**:
    - Count the number of employees whose performance rating is NULL.
    - Find the total bonus amount where the department is not NULL.


# Solution Query
---

### 1. **What is the total salary for each department?**
```sql
SELECT Department, SUM(Salary) AS Total_Salary
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
We use `GROUP BY Department` to group employees by their department, and `SUM(Salary)` aggregates the total salary for each department.

---

### 2. **How many employees are there in each department?**
```sql
SELECT Department, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
The `COUNT(Employee_ID)` function returns the number of employees in each department. The `GROUP BY` clause groups the data by department.

---

### 3. **What is the average salary in each department?**
```sql
SELECT Department, AVG(Salary) AS Average_Salary
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
Here, we use `AVG(Salary)` to calculate the average salary for each department.

---

### 4. **How many employees are in each city?**
```sql
SELECT City, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The query groups employees by city and counts how many employees are in each city using `COUNT(Employee_ID)`.

---

### 5. **What is the count of employees in each job title?**
```sql
SELECT Job_Title, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY Job_Title;
```
**Explanation:**  
This query calculates the number of employees for each job title.

---

### 6. **How many employees have a performance rating of 4?**
```sql
SELECT COUNT(Employee_ID) AS Employees_With_Rating_4
FROM Employee_Salaries
WHERE Performance_Rating = 4;
```
**Explanation:**  
The `COUNT(Employee_ID)` counts the employees with a performance rating of 4 using a `WHERE` clause.

---

### 7. **How many employees in the 'Sales' department have more than 20 days of attendance?**
```sql
SELECT COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
WHERE Department = 'Sales' AND Attendance > 20;
```
**Explanation:**  
The query counts employees in the 'Sales' department with more than 20 days of attendance using the `WHERE` clause to filter both conditions.

---

### 8. **What is the total bonus amount for each department?**
```sql
SELECT Department, SUM(Bonus) AS Total_Bonus
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
We use `SUM(Bonus)` to calculate the total bonus for each department, grouped by department.

---

### 9. **What is the total salary paid for employees in each city?**
```sql
SELECT City, SUM(Salary) AS Total_Salary
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The query groups the employees by city and sums the salaries within each city.

---

### 10. **What is the total overtime hours worked by employees in each department?**
```sql
SELECT Department, SUM(Overtime_Hours) AS Total_Overtime_Hours
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
This query calculates the total overtime hours for each department.

---

### 11. **What is the average bonus amount for employees in each department?**
```sql
SELECT Department, AVG(Bonus) AS Average_Bonus
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
The query uses `AVG(Bonus)` to calculate the average bonus amount for each department.

---

### 12. **What is the average salary of employees for each job title?**
```sql
SELECT Job_Title, AVG(Salary) AS Average_Salary
FROM Employee_Salaries
GROUP BY Job_Title;
```
**Explanation:**  
The query groups by `Job_Title` and calculates the average salary for each job title.

---

### 13. **What is the average experience (in years) for employees in each city?**
```sql
SELECT City, AVG(Experience) AS Average_Experience
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The query calculates the average experience (in years) of employees in each city.

---

### 14. **What is the minimum salary in each department?**
```sql
SELECT Department, MIN(Salary) AS Minimum_Salary
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
`MIN(Salary)` calculates the minimum salary in each department.

---

### 15. **What is the maximum salary in each city?**
```sql
SELECT City, MAX(Salary) AS Maximum_Salary
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The `MAX(Salary)` function finds the highest salary in each city.

---

### 16. **What is the highest performance rating by job title?**
```sql
SELECT Job_Title, MAX(Performance_Rating) AS Highest_Performance_Rating
FROM Employee_Salaries
GROUP BY Job_Title;
```
**Explanation:**  
This query finds the highest performance rating for each job title.

---

### 17. **Which departments have an average salary greater than 70,000?**
```sql
SELECT Department
FROM Employee_Salaries
GROUP BY Department
HAVING AVG(Salary) > 70000;
```
**Explanation:**  
The `HAVING` clause filters departments where the average salary is greater than 70,000.

---

### 18. **Which city has an average attendance of more than 20 days per employee?**
```sql
SELECT City
FROM Employee_Salaries
GROUP BY City
HAVING AVG(Attendance) > 20;
```
**Explanation:**  
This query filters cities where the average attendance is greater than 20 days.

---

### 19. **Which job title has more than 5 employees with a performance rating of 4 or higher?**
```sql
SELECT Job_Title
FROM Employee_Salaries
WHERE Performance_Rating >= 4
GROUP BY Job_Title
HAVING COUNT(Employee_ID) > 5;
```
**Explanation:**  
The `HAVING` clause filters job titles with more than 5 employees whose performance rating is 4 or higher.

---

### 20. **How many distinct cities do employees work in?**
```sql
SELECT COUNT(DISTINCT City) AS Distinct_Cities
FROM Employee_Salaries;
```
**Explanation:**  
`COUNT(DISTINCT City)` counts the distinct cities in which employees work.

---

### 21. **How many distinct job titles are there in the company?**
```sql
SELECT COUNT(DISTINCT Job_Title) AS Distinct_Job_Titles
FROM Employee_Salaries;
```
**Explanation:**  
This counts the distinct job titles in the table.

---

### 22. **What is the average salary and total bonus for each department?**
```sql
SELECT Department, AVG(Salary) AS Average_Salary, SUM(Bonus) AS Total_Bonus
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
We use `AVG(Salary)` to find the average salary and `SUM(Bonus)` to find the total bonus for each department.

---

### 23. **What is the total salary and total overtime worked by employees in each city?**
```sql
SELECT City, SUM(Salary) AS Total_Salary, SUM(Overtime_Hours) AS Total_Overtime
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The query groups by city and sums both salary and overtime hours.

---

### 24. **What is the average performance rating and minimum attendance for employees in each department?**
```sql
SELECT Department, AVG(Performance_Rating) AS Average_Performance_Rating, MIN(Attendance) AS Min_Attendance
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
This groups by department and calculates the average performance rating and minimum attendance for each department.

---

### 25. **What is the average salary of employees hired in each year?**
```sql
SELECT YEAR(Hire_Date) AS Hire_Year, AVG(Salary) AS Average_Salary
FROM Employee_Salaries
GROUP BY YEAR(Hire_Date);
```
**Explanation:**  
The `YEAR(Hire_Date)` function extracts the year of hire, and we group by year to calculate the average salary of employees hired in each year.

---

### 26. **How many employees joined in each month of the year?**
```sql
SELECT MONTH(Hire_Date) AS Hire_Month, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY MONTH(Hire_Date);
```
**Explanation:**  
The query groups employees by the month of their hire date and counts them for each month.

---

### 27. **What is the average experience of employees hired in 2019?**
```sql
SELECT AVG(Experience) AS Average_Experience
FROM Employee_Salaries
WHERE YEAR(Hire_Date) = 2019;
```
**Explanation:**  
This calculates the average experience of employees hired in 2019 using a `WHERE` clause to filter the year.

---

### 28. **What is the average salary for each combination of department and job title?**
```sql
SELECT Department, Job_Title, AVG(Salary) AS Average_Salary
FROM Employee_Salaries
GROUP BY Department, Job_Title;
```
**Explanation:**  
The query groups employees by both department and job title to find the average salary for each combination.

---

### 29. **What is the total salary for each combination of city and gender?**
```sql
SELECT City, Gender, SUM(Salary) AS Total_Salary
FROM Employee_Salaries
GROUP BY City, Gender;
```
**Explanation:**  
This groups the data by both city and gender, and calculates the total salary for each combination.

---

### 30. **What is the average attendance by department and gender?**
```sql
SELECT Department, Gender, AVG(Attendance) AS Average_Attendance
FROM Employee_Salaries
GROUP BY Department, Gender;
```
**Explanation:**  
The query groups by department and gender, and calculates the average attendance for each combination.

---

### 31. **Which departments have an average salary greater than 60,000 and fewer than 5 employees?**
```sql
SELECT Department
FROM Employee_Salaries
GROUP BY Department
HAVING AVG(Salary) > 60000 AND COUNT(Employee_ID) < 5;
```
**Explanation:**  
This uses `HAVING` to filter departments with an average salary above 60,000 and fewer than 5 employees.

---

### 32. **Which departments have more than 3 employees with a performance rating greater than 3?**
```sql
SELECT Department
FROM Employee_Salaries
WHERE Performance_Rating > 3
GROUP BY Department
HAVING COUNT(Employee_ID) > 3;
```
**Explanation:**  
The query counts employees with a performance rating greater than 3, grouped by department, and filters departments with more than 3 such employees.

---

### 33. **What is the department with the highest average salary from employees with more than 3 years of experience?**
```sql
SELECT Department
FROM Employee_Salaries
WHERE Experience > 3
GROUP BY Department
ORDER BY AVG(Salary) DESC
LIMIT 1;
```
**Explanation:**  
This query filters employees with more than 3 years of experience and orders departments by average salary in descending order, selecting the one with the highest average salary.

---

### 34. **What is the city with the lowest total salary, considering only employees with over 4 years of experience?**
```sql
SELECT City
FROM Employee_Salaries
WHERE Experience > 4
GROUP BY City
ORDER BY SUM(Salary) ASC
LIMIT 1;
```
**Explanation:**  
The query groups by city and calculates the total salary for employees with more than 4 years of experience, ordering the results to find the city with the lowest total salary.

---

### 35. **List the departments with total salary amounts in descending order.**
```sql
SELECT Department, SUM(Salary) AS Total_Salary
FROM Employee_Salaries
GROUP BY Department
ORDER BY Total_Salary DESC;
```
**Explanation:**  
This query groups the data by department, calculates the total salary, and orders the results in descending order of total salary.

---

### 36. **List the cities with the most employees in ascending order.**
```sql
SELECT City, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY City
ORDER BY Employee_Count ASC;
```
**Explanation:**  
The query groups by city and counts the number of employees in each city, ordering the cities by employee count in ascending order.

---

### 37. **What is the total salary, average salary, and the count of employees for each job title?**
```sql
SELECT Job_Title, SUM(Salary) AS Total_Salary, AVG(Salary) AS Average_Salary, COUNT(Employee_ID) AS Employee_Count
FROM Employee_Salaries
GROUP BY Job_Title;
```
**Explanation:**  
This query calculates the total salary, average salary, and employee count for each job title.

---

### 38. **Which departments have the highest average bonus, and what is the average bonus amount?**
```sql
SELECT Department, AVG(Bonus) AS Average_Bonus
FROM Employee_Salaries
GROUP BY Department
ORDER BY Average_Bonus DESC
LIMIT 1;
```
**Explanation:**  
The query calculates the average bonus for each department and orders by average bonus in descending order to find the department with the highest average bonus.

---

### 39. **Which employee has the highest salary in each department?**
```sql
SELECT Department, Employee_ID, MAX(Salary) AS Highest_Salary
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
This query finds the employee with the highest salary in each department by grouping by department and using `MAX(Salary)`.

---

### 40. **What is the highest performance rating in each city?**
```sql
SELECT City, MAX(Performance_Rating) AS Highest_Performance_Rating
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
The query calculates the highest performance rating for employees in each city.

---

### 41. **Find the total salary and total overtime hours worked by employees who have more than 10 overtime hours.**
```sql
SELECT SUM(Salary) AS Total_Salary, SUM(Overtime_Hours) AS Total_Overtime
FROM Employee_Salaries
WHERE Overtime_Hours > 10;
```
**Explanation:**  
The `WHERE` clause filters employees who worked more than 10 overtime hours, and the query calculates their total salary and overtime hours.

---

### 42. **Find the average age and average salary for employees who have attended more than 20 days.**
```sql
SELECT AVG(Age) AS Average_Age, AVG(Salary) AS Average_Salary
FROM Employee_Salaries
WHERE Attendance > 20;
```
**Explanation:**  
This query calculates the average age and average salary for employees who attended more than 20 days.

---

### 43. **Find the department with the maximum attendance.**
```sql
SELECT Department
FROM Employee_Salaries
GROUP BY Department
ORDER BY SUM(Attendance) DESC
LIMIT 1;
```
**Explanation:**  
The query calculates the total attendance for each department and orders by attendance in descending order to find the department with the maximum attendance.

---

### 44. **Find the employee with the lowest salary in each department.**
```sql
SELECT Department, Employee_ID, MIN(Salary) AS Lowest_Salary
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
This query finds the employee with the lowest salary in each department by using the `MIN(Salary)` function.

---

### 45. **What is the average experience for employees in each department?**
```sql
SELECT Department, AVG(Experience) AS Average_Experience
FROM Employee_Salaries
GROUP BY Department;
```
**Explanation:**  
This query calculates the average experience (in years) for employees in each department.

---

### 46. **What is the total bonus and total salary for each department with more than 4 employees?**
```sql
SELECT Department, SUM(Bonus) AS Total_Bonus, SUM(Salary) AS Total_Salary
FROM Employee_Salaries
GROUP BY Department
HAVING COUNT(Employee_ID) > 4;
```
**Explanation:**  
The query calculates the total salary and total bonus for departments that have more than 4 employees.

---

### 47. **Which departments have an average performance rating of less than 4?**
```sql
SELECT Department
FROM Employee_Salaries
GROUP BY Department
HAVING AVG(Performance_Rating) < 4;
```
**Explanation:**  
The query filters departments that have an average performance rating of less than 4.

---

### 48. **What is the total salary and total bonus for each city?**
```sql
SELECT City, SUM(Salary) AS Total_Salary, SUM(Bonus) AS Total_Bonus
FROM Employee_Salaries
GROUP BY City;
```
**Explanation:**  
This query groups the employees by city and calculates both the total salary and the total bonus for each city.

---

### 49. **Find the job title with the highest average salary.**
```sql
SELECT Job_Title
FROM Employee_Salaries
GROUP BY Job_Title
ORDER BY AVG(Salary) DESC
LIMIT 1;
```
**Explanation:**  
This query calculates the average salary for each job title and returns the one with the highest average salary.

---

### 50. **Which department has the most employees with performance ratings higher than 3?**
```sql
SELECT Department
FROM Employee_Salaries
WHERE Performance_Rating > 3
GROUP BY Department
ORDER BY COUNT(Employee_ID) DESC
LIMIT 1;
```
**Explanation:**  
This query filters employees with a performance rating greater than 3, groups by department, and orders by employee count to find the department with the most such employees.

---