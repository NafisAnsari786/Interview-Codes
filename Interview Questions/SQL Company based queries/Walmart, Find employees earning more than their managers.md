<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Walmart (Medium Level) hashtag#SQL Interview Question — Solution

Find employees who are earning more than their managers. Output the employee's first name along with the corresponding salary.

🌀 Trust me, this one easiest one if you know self join concept, if not will surely challenge you...! Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE employee_detail (id BIGINT PRIMARY KEY, first_name VARCHAR(100), last_name VARCHAR(100), address VARCHAR(255), age BIGINT, bonus BIGINT, city VARCHAR(100), department VARCHAR(100), email VARCHAR(100), employee_title VARCHAR(100), manager_id BIGINT, salary BIGINT, sex VARCHAR(10), target BIGINT);

INSERT INTO employee_detail (id, first_name, last_name, address, age, bonus, city, department, email, employee_title, manager_id, salary, sex, target) VALUES (1, 'John', 'Doe', '123 Main St', 45, 5000, 'New York', 'IT', 'john.doe@example.com', 'Manager', NULL, 90000, 'M', 50000), (2, 'Jane', 'Smith', '456 Elm St', 38, 3000, 'Los Angeles', 'IT', 'jane.smith@example.com', 'Senior Developer', 1, 95000, 'F', 60000), (3, 'Alice', 'Johnson', '789 Oak St', 30, 2000, 'Chicago', 'HR', 'alice.johnson@example.com', 'HR Specialist', 1, 80000, 'F', 40000), (4, 'Bob', 'Brown', '321 Pine St', 40, 4000, 'Miami', 'Finance', 'bob.brown@example.com', 'Finance Manager', NULL, 85000, 'M', 45000), (5, 'Charlie', 'Davis', '654 Cedar St', 28, 1500, 'Seattle', 'Finance', 'charlie.davis@example.com', 'Analyst', 4, 88000, 'M', 55000), (6, 'Eve', 'Wilson', '987 Maple St', 35, 2500, 'Boston', 'Marketing', 'eve.wilson@example.com', 'Marketing Specialist', 4, 84000, 'F', 50000);

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Self-Join: The table is joined with itself to compare employees with their managers. e is the alias for the employee, and m is the alias for the manager.

2. Condition: The ON e.manager_id = m.id condition ensures that we match each employee with their corresponding manager.

3. Filter: The WHERE e.salary > m.salary condition filters out employees who earn more than their managers.

**SOLUTION**

<img width="798" height="378" alt="image" src="https://github.com/user-attachments/assets/5b2acd5f-31ad-479b-81c7-462b7d7ea33d" />
