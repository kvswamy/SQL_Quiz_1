# SQL_Quiz_1


1. Write an SQL query to select all columns from a table named "employees."

2. Write an SQL query to select the "name" and "salary" columns from a table named "workers."

3. Retrieve all records from a table named "students" where the "age" is greater than 21.

4. Write an SQL query to retrieve data from a table named "products" and order it by the "price" column in descending order.

5. Calculate the number of rows in a table named "orders."

6. Write an SQL query to count the number of employees in the "sales" department from a table named "employees."

7. Select all columns from the "orders" table along with the "customer_name" from the "customers" table, joining them on the "customer_id" column.

8. Calculate the average salary of employees in each department from a table named "employee_details."

9. Retrieve all employees from the "managers" table whose salary is greater than the average salary of employees in the "employees" table.

10. Update the "status" column to 'Shipped' for all records in the "orders" table where the "order_date" is before '2023-01-01.'




 
Table reference for questions 11-15

**Table: customers**

Customer_id	Customer_name	Registration_date	Referred_by
1	Alice	2022-01-10	
2	Bob	2022-02-15	5
3	Carol	2022-03-20	5
4	Dave	2022-04-05	
5	Eve	2022-05-01	1


**Table: orders**

Order_id	Customer_id	Order_date	Status
1	1	2022-03-10	Pending
2	2	2022-04-15	Shipped
3	3	2022-05-20	Pending
4	1	2022-06-20	Shipped
5	4	2022-07-01	Pending


11. Write an SQL query to find the customer(s) who placed the most orders.

12. Create a query to find all customers who referred other customers. The "referred_by" column in the "customers" table contains the customer_id of the referring customer. 

13. Remove all orders with a status of "Pending"

14. Write a query to find all customers who have not placed any orders.

15. Retrieve a list of customers with status of ”Success”, along with the total number of orders each customer has placed.
 
Answers:
1. `SELECT * FROM employees;`
2. `SELECT name, salary FROM workers;`
3. `SELECT * FROM students WHERE age > 21;`
4. `SELECT * FROM products ORDER BY price DESC;`
5. `SELECT COUNT(*) FROM orders;`
6. `SELECT COUNT(*) FROM employees WHERE department = 'sales';`
7. `SELECT orders.*, customers.customer_name FROM orders INNER JOIN customers ON orders.customer_id = customers.customer_id;`
8. `SELECT department, AVG(salary) FROM employee_details GROUP BY department;`
9. `SELECT * FROM managers WHERE salary > (SELECT AVG(salary) FROM employees);`
10. `UPDATE orders SET status = 'Shipped' WHERE order_date < '2023-01-01';`
11. SELECT Customer_name 
FROM customers INNER JOIN orders ON customers.customer_id=orders.customer_id 
GROUP BY Customer_name 
ORDER BY COUNT(order_id) DESC 
LIMIT 1
12. SELECT c1.customer_name, c2.customer_name referral_name
FROM customers c1 LEFT JOIN customers c2 ON c1.referred_by=c2.customer_id
13. DELETE FROM orders WHERE Status=’Pending’
14. SELECT * FROM customers WHERE customer_id NOT IN (SELECT customer_id FROM orders)
15. SELECT customers.Customer_name, count(*)
FROM customers inner join orders
ON customers.customer_id=orders.customer_id
WHERE Status=’Shipped’
GROUP BY Customer_name



# SQL_Quiz_1
