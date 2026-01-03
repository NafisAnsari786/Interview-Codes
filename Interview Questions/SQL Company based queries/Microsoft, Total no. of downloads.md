<img src="https://img.shields.io/badge/HARD-darkred" alt="HARD" width="70">

𝐌𝐮𝐬𝐭 𝐓𝐫𝐲: Microsoft (Hard Level) hashtag#SQL Interview Question — Solution

Find the total number of downloads for paying and non-paying users by date. Include only records where non-paying customers have more downloads than paying customers. The output should be sorted by earliest date first and contain 3 columns date, non-paying downloads, paying downloads. 

Note: In Oracle you should use "date" when referring to date column (reserved keyword).

🔍By solving this, you'll learn how to use join, groupby and having. Give it a try and share the output!👇

𝐒𝐜𝐡𝐞𝐦𝐚 𝐚𝐧𝐝 𝐃𝐚𝐭𝐚𝐬𝐞𝐭:
CREATE TABLE ms_user_dimension (user_id INT PRIMARY KEY,acc_id INT);
INSERT INTO ms_user_dimension (user_id, acc_id) VALUES (1, 101),(2, 102),(3, 103),(4, 104),(5, 105);

CREATE TABLE ms_acc_dimension (acc_id INT PRIMARY KEY,paying_customer VARCHAR(10));
INSERT INTO ms_acc_dimension (acc_id, paying_customer) VALUES (101, 'Yes'),(102, 'No'),(103, 'Yes'),(104, 'No'),(105, 'No');

CREATE TABLE ms_download_facts (date DATETIME,user_id INT,downloads INT);
INSERT INTO ms_download_facts (date, user_id, downloads) VALUES ('2024-10-01', 1, 10),('2024-10-01', 2, 15),('2024-10-02', 1, 8),('2024-10-02', 3, 12),('2024-10-02', 4, 20),('2024-10-03', 2, 25),('2024-10-03', 5, 18);
-----------

I have provided an explanation and query, but I encourage you to try solving it first. Later, you can check the query for reference.

𝐄𝐱𝐩𝐥𝐚𝐧𝐚𝐭𝐢𝐨𝐧 𝐭𝐨 𝐒𝐨𝐥𝐯𝐞 𝐐𝐮𝐞𝐫𝐲
1. CONVERT(DATE, d.date): We convert the datetime to date to ensure we’re aggregating by date only.

2. SUM with CASE: The CASE within SUM helps in counting downloads conditionally:
For non-paying customers (a.paying_customer = 'No'), it sums downloads only when the customer is non-paying.
For paying customers (a.paying_customer = 'Yes'), it sums downloads only when the customer is paying.

3. HAVING Clause: Filters results to include only dates where non-paying customers have more downloads than paying customers.

4. ORDER BY [date] ASC: Orders the output by the date in ascending order, as required.

**SOLUTION**

<img width="800" height="462" alt="image" src="https://github.com/user-attachments/assets/2d7b0750-7844-4cc5-903f-7a35f8a1664b" />

