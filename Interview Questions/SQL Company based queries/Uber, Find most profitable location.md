<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Uber (Hard Level) hashtag#SQL Interview Question — Solution

Find the most profitable location. Write a query that calculates the average signup duration and average transaction amount for each location, and then compare these two measures together by taking the ratio of the average transaction amount and average duration for each location.

Your output should include the location, average duration, average transaction amount, and ratio. Sort your results from highest ratio to lowest.

🔍By solving this, you'll learn how to use CTE, Join, Group By, Having, Case, Avg. Give it a try and share the output! 👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭
CREATE TABLE signups (signup_id INT PRIMARY KEY, signup_start_date DATETIME, signup_stop_date DATETIME, plan_id INT, location VARCHAR(100));

INSERT INTO signups (signup_id, signup_start_date, signup_stop_date, plan_id, location) VALUES (1, '2020-01-01 10:00:00', '2020-01-01 12:00:00', 101, 'New York'), (2, '2020-01-02 11:00:00', '2020-01-02 13:00:00', 102, 'Los Angeles'), (3, '2020-01-03 10:00:00', '2020-01-03 14:00:00', 103, 'Chicago'), (4, '2020-01-04 09:00:00', '2020-01-04 10:30:00', 101, 'San Francisco'), (5, '2020-01-05 08:00:00', '2020-01-05 11:00:00', 102, 'New York');

CREATE TABLE transactions (transaction_id INT PRIMARY KEY,signup_id INT,transaction_start_date DATETIME,amt FLOAT,FOREIGN KEY (signup_id) REFERENCES signups(signup_id));

INSERT INTO transactions (transaction_id, signup_id, transaction_start_date, amt) VALUES (1, 1, '2020-01-01 10:30:00', 50.00), (2, 1, '2020-01-01 11:00:00', 30.00), (3, 2, '2020-01-02 11:30:00', 100.00), (4, 2, '2020-01-02 12:00:00', 75.00), (5, 3, '2020-01-03 10:30:00', 120.00), (6, 4, '2020-01-04 09:15:00', 80.00), (7, 5, '2020-01-05 08:30:00', 90.00);

---------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. SignupDurations CTE: Calculates the signup duration in minutes for each signup by taking the difference between signup_start_date and signup_stop_date

2. TransactionAmounts CTE: Calculates the average transaction amount for each signup by grouping transactions by signup_id

3. Main Query: Joins the results of SignupDurations & TransactionAmounts on signup_id. Groups data by location to compute: Average signup duration, Average transaction amount. Ratio of average transaction amount to average signup duration.

Handles cases where signup duration is zero to avoid division errors.

**SOLUTION**

<img width="800" height="696" alt="image" src="https://github.com/user-attachments/assets/76605f4d-e800-4c93-8c48-0d222d55f9a2" />
