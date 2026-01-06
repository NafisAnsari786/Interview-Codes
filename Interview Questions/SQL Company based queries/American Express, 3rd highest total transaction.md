<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Walmart, Paypal (Medium Level) hashtag#SQL Interview Question — Solution

Find managers with at least 7 direct reporting employees. In situations where user is reporting to himself/herself, count that also.
Output first names of managers.

🔍By solving this, you'll learn how to use self join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE employees (id INT PRIMARY KEY,first_name VARCHAR(50),last_name VARCHAR(50),age INT,sex VARCHAR(10),employee_title VARCHAR(50),department VARCHAR(50),salary INT,target INT,bonus INT,email VARCHAR(100),city VARCHAR(50),address VARCHAR(255),manager_id INT);

INSERT INTO employees (id, first_name, last_name, age, sex, employee_title, department, salary, target, bonus, email, city, address, manager_id) VALUES(1, 'Alice', 'Smith', 40, 'F', 'Manager', 'Sales', 90000, 100000, 15000, 'alice.smith@example.com', 'New York', '123 Main St', 1),(2, 'Bob', 'Johnson', 35, 'M', 'Team Lead', 'Sales', 80000, 95000, 12000, 'bob.johnson@example.com', 'Chicago', '456 Oak St', 1),(3, 'Carol', 'Williams', 30, 'F', 'Sales Executive', 'Sales', 70000, 85000, 10000, 'carol.williams@example.com', 'New York', '789 Pine St', 1),(4, 'David', 'Brown', 28, 'M', 'Sales Executive', 'Sales', 68000, 80000, 9000, 'david.brown@example.com', 'Chicago', '101 Maple St', 1),(5, 'Emma', 'Jones', 32, 'F', 'Sales Executive', 'Sales', 71000, 86000, 9500, 'emma.jones@example.com', 'New York', '202 Cedar St', 1),(6, 'Frank', 'Miller', 45, 'M', 'Manager', 'Engineering', 95000, 105000, 16000, 'frank.miller@example.com', 'San Francisco', '303 Spruce St', 6),(7, 'Grace', 'Davis', 29, 'F', 'Engineer', 'Engineering', 73000, 87000, 11000, 'grace.davis@example.com', 'San Francisco', '404 Willow St', 6);
-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Self-reporting Employees: Since manager_id points back to the id column in the same table, cases where manager_id = id (self-reporting) are automatically included.

2. JOIN: The query joins the employees table with itself to match employees (e) with their managers (m) based on manager_id.

3. COUNT and HAVING: After grouping by the manager’s id, HAVING COUNT(e.id) >= 7 filters for managers with at least 7 direct reports.

**SOLUTION**

<img width="750" height="462" alt="image" src="https://github.com/user-attachments/assets/03421344-a0ac-46f2-97f4-1ec961505062" />


𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: American Express (Medium Level) hashtag#SQL Interview Question — Solution

American Express is reviewing their customers' transactions, and you have been tasked with locating the customer who has the third highest total transaction amount. The output should include the customer's id, as well as their first name and last name. For ranking the customers, use type of ranking with no gaps between subsequent ranks.

🔍By solving this, you'll learn how to use mutiple join. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE customers (id INT,first_name VARCHAR(50),last_name VARCHAR(50),city VARCHAR(100),address VARCHAR(200),phone_number VARCHAR(20));

INSERT INTO customers (id, first_name, last_name, city, address, phone_number) VALUES(1, 'Jill', 'Doe', 'New York', '123 Main St', '555-1234'),(2, 'Henry', 'Smith', 'Los Angeles', '456 Oak Ave', '555-5678'),(3, 'William', 'Johnson', 'Chicago', '789 Pine Rd', '555-8765'),(4, 'Emma', 'Daniel', 'Houston', '321 Maple Dr', '555-4321'),(5, 'Charlie', 'Davis', 'Phoenix', '654 Elm St', '555-6789');

CREATE TABLE card_orders (order_id INT,cust_id INT,order_date DATETIME,order_details VARCHAR(255),total_order_cost INT);

INSERT INTO card_orders (order_id, cust_id, order_date, order_details, total_order_cost) VALUES(1, 1, '2024-11-01 10:00:00', 'Electronics', 200),(2, 2, '2024-11-02 11:30:00', 'Groceries', 150),(3, 1, '2024-11-03 15:45:00', 'Clothing', 120),(4, 3, '2024-11-04 09:10:00', 'Books', 90),(8, 3, '2024-11-08 10:20:00', 'Groceries', 130),(9, 1, '2024-11-09 12:00:00', 'Books', 180),(10, 4, '2024-11-10 11:15:00', 'Electronics', 200),(11, 5, '2024-11-11 14:45:00', 'Furniture', 150),(12, 2, '2024-11-12 09:30:00', 'Furniture', 180);
-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. CustomerTransactionTotals CTE: Aggregates each customer's total transaction amount by summing total_order_cost for each cust_id.

2. RankedTransactions CTE: Ranks customers based on total_transaction_amount using RANK() with no gaps in ranking.

3. Final Selection: Selects the customer with transaction_rank = 3 to retrieve the customer with the third-highest transaction total, including their ID, first name, and last name.

**SOLUTION**

<img width="800" height="676" alt="image" src="https://github.com/user-attachments/assets/0b260684-1933-4b8e-801e-fc8c162fd130" />
