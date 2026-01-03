<img src="https://img.shields.io/badge/MEDIUM-orange" alt="MEDIUM" width="70">

𝐓𝐫𝐲 𝐋𝐚𝐭𝐞𝐫: LinkedIn, Dropbox (Basic Level) hashtag#SQL Interview Question — Solution

Write a query that calculates the difference between the highest salaries found in the marketing and engineering departments. Output just the absolute difference in salaries.

🔍 By solving this, you'll learn how to use case and join. Give it a try later and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE db_employee (id INT,first_name VARCHAR(50),last_name VARCHAR(50),salary INT,department_id INT);

INSERT INTO db_employee (id, first_name, last_name, salary, department_id) VALUES(10306, 'Ashley', 'Li', 28516, 4),(10307, 'Joseph', 'Solomon', 19945, 1),(10311, 'Melissa', 'Holmes', 33575, 1),(10316, 'Beth', 'Torres', 34902, 1),(10317, 'Pamela', 'Rodriguez', 48187, 4),(10320, 'Gregory', 'Cook', 22681, 4),(10324, 'William', 'Brewer', 15947, 1),(10329, 'Christopher', 'Ramos', 37710, 4),(10333, 'Jennifer', 'Blankenship', 13433, 4),(10339, 'Robert', 'Mills', 13188, 1);

CREATE TABLE db_dept (id INT,department VARCHAR(50));

INSERT INTO db_dept (id, department) VALUES(1, 'engineering'),(2, 'human resource'),(3, 'operation'),(4, 'marketing');
------------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. CASE is used to selectively get the salary for the "marketing" and "engineering" departments.
2. MAX is applied to retrieve the highest salary in each department.
3. ABS calculates the absolute difference between the two maximum values.

**SOLUTION**

<img width="800" height="384" alt="image" src="https://github.com/user-attachments/assets/2a44ce5f-601d-4717-9a3f-2cab7dff33ff" />
