<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Uber (Hard Level) hashtag#SQL Interview Question — Solution

Find the most profitable location. Write a query that calculates the average signup duration and average transaction amount for each location, and then compare these two measures together by taking the ratio of the average transaction amount and average duration for each location.

Your output should include the location, average duration, average transaction amount, and ratio. Sort your results from highest ratio to lowest.

🌀 Trust me, this one will surely challenge you...! You'll learn Agg function, Joins, Group by. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE cust_signups (location VARCHAR(100), plan_id BIGINT, signup_id BIGINT PRIMARY KEY, signup_start_date DATETIME, signup_stop_date DATETIME);

INSERT INTO cust_signups (location, plan_id, signup_id, signup_start_date, signup_stop_date) VALUES  ('New York', 101, 1, '2025-01-01', '2025-01-31'), ('San Francisco', 102, 2, '2025-01-05', '2025-02-05'), ('Los Angeles', 103, 3, '2025-01-10', '2025-01-20'), ('New York', 104, 4, '2025-02-01', '2025-02-28'), ('Los Angeles', 105, 5, '2025-01-15', '2025-01-25');

CREATE TABLE cust_transactions (amt FLOAT, signup_id BIGINT, transaction_id BIGINT PRIMARY KEY, transaction_start_date DATETIME);

INSERT INTO cust_transactions (amt, signup_id, transaction_id, transaction_start_date) VALUES (100.50, 1, 1001, '2025-01-10'), (200.75, 1, 1002, '2025-01-20'), (150.00, 2, 1003, '2025-01-15'), (300.00, 3, 1004, '2025-01-12'), (400.00, 4, 1005, '2025-02-15'), (250.00, 5, 1006, '2025-01-20');

---------

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. Calculated the duration directly using DATEDIFF or other function.

2. Used AVG directly for both duration and transaction amount.

3. Incorporated the ratio calculation directly in the SELECT statement.

**SOLUTION**

<img width="800" height="513" alt="image" src="https://github.com/user-attachments/assets/3220aa50-a7fe-411c-9b38-d76347bd4484" />

