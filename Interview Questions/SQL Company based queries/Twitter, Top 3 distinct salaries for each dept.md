<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Twitter(Hard Level) hashtag#SQL Interview Question — Solution

Find the top three distinct salaries for each department. Output the department name and the top 3 distinct salaries by each department. Order your results alphabetically by department and then by highest salary to lowest.

🔍By solving this, you'll learn how to use CTE, Group By, Having, Case. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE employees (id INT PRIMARY KEY,first_name VARCHAR(50), last_name VARCHAR(50), age INT, sex VARCHAR(1), employee_title VARCHAR(50), department VARCHAR(50), salary INT, target INT, bonus INT, city VARCHAR(50), address VARCHAR(50), manager_id INT);

INSERT INTO employees (id, first_name, last_name, age, sex, employee_title, department, salary, target, bonus, city, address, manager_id) VALUES (1, 'Allen', 'Wang', 55, 'F', 'Manager', 'Management', 200000, 0, 300, 'California', '23St', 1),(13, 'Katty', 'Bond', 56, 'F', 'Manager', 'Management', 150000, 0, 300, 'Arizona', NULL, 1),(19, 'George', 'Joe', 50, 'M', 'Manager', 'Management', 100000, 0, 300, 'Florida', '26St', 1),(11, 'Richerd', 'Gear', 57, 'M', 'Manager', 'Management', 250000, 0, 300, 'Alabama', NULL, 1),(10, 'Jennifer', 'Dion', 34, 'F', 'Sales', 'Sales', 100000, 200, 150, 'Alabama', NULL, 13),(18, 'Laila', 'Mark', 26, 'F', 'Sales', 'Sales', 100000, 200, 150,  'Florida', '23St', 11),(20, 'Sarrah', 'Bicky', 31, 'F', 'Senior Sales', 'Sales', 200000, 200, 150, 'Florida', '53St', 19),(21, 'Suzan', 'Lee', 34, 'F', 'Sales', 'Sales', 130000, 200, 150,  'Florida', '56St', 19),(22, 'Mandy', 'John', 31, 'F', 'Sales', 'Sales', 130000, 200, 150,  'Florida', '45St', 19),(17, 'Mick', 'Berry', 44, 'M', 'Senior Sales', 'Sales', 220000, 200, 150, 'Florida', NULL, 11),(12, 'Shandler', 'Bing', 23, 'M', 'Auditor', 'Audit', 110000, 200, 150, 'Arizona', NULL, 11),(14, 'Jason', 'Tom', 23, 'M', 'Auditor', 'Audit', 100000, 200, 150, 'Arizona', NULL, 11),(16, 'Celine', 'Anston', 27, 'F', 'Auditor', 'Audit', 100000, 200, 150, 'Colorado', NULL, 11),(15, 'Michale', 'Jackson', 44, 'F', 'Auditor', 'Audit', 70000, 150, 150, 'Colorado', NULL, 11),(6, 'Molly', 'Sam', 28, 'F', 'Sales', 'Sales', 140000, 100, 150, 'Arizona', '24St', 13),(7, 'Nicky', 'Bat', 33, 'F', 'Sales', 'Sales', NULL, NULL, NULL, NULL, NULL, NULL);
---------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. GROUP BY department, salary ensures only distinct salaries are considered within each department.

**SOLUTION**

<img width="800" height="629" alt="image" src="https://github.com/user-attachments/assets/bc8af3ef-12c9-4f94-9fe3-5246026bcef0" />
